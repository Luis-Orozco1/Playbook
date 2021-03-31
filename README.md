Role Name<br>
OcpNodos
=========
# Configuracion para nuevos nodos de Openshift.
Descripción.
-
<p>
Realiza la configuracion para crear nuevos nodos de Openshift,
que va desde la subscripción con Red Hat de tu sistema operativo 
hasta la creacion de un usuario Openshift.<br>
Nuestro playbook fue desarrollado utilizando roles, ya que los roles
siguen una estructura de directorios que nos ayudan a tener un control
en la configuracion de nuestro playbook.
</p>


Requirements
------------
Para poder ejecutar este playbook, es necesario: <br>
- Contar con Ansible en tu equipo.<br>
- Una terminal <br>
- [Guia de instalacion para Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) 

Si deseas ejecutar este playbook en un servidor externo al tuyo
necesitas: <br>
- Que tu equipo cuente con Ansible.<br>
- Tener acceso via ssh al servidor que quieras gestionar.<br>
- Contar con un inventario de los nodos gestionados (hosts)<br>
- Una terminal<br>


Role Variables
--------------
<p>
En esta parte definimos las variables que vamos a utilizar al 
momento de ejecutar una tarea en nuestro playbook.
Por ejemplo, en este playbook vamos a ocupar 4 variables, 2 cuando se realice
la subscripción de tu sistema a Red Hat y las otras 2 al 
momento de crear el usuario Openshift.</p>
Ejemplo:
<pre>
vars:
  username: 'Administrador'
  password: 'Contraseña'
</pre>

Y en la tarea se veria algo como lo siguiente:
<pre>
- name: subscription-manager
    redhat_subscription:
      state: present
      username: {{username}}
      password: {{password}}
</pre>
 


Example Playbook
----------------
A continuacion, se muestra un ejemplo del playbook utilizando roles.<br>
<pre>
---
- name: Preparar nuevos nodos de Openshift
  hosts: host3
  remote_user: Administrador
  roles:
  - OcpNodos

</pre>
<p> Como podemos observar en el ejemplo, definimos un nombre para nuestro playbook
en la parte de <code>- name </code>, definimos un host al cual nos queramos conectar,
ponemos el nombre del usuario remoto del servidor y ya por ultimo definimos el nombre
del rol que vamos a utilizar en este caso <code>- OcpNodos </code>.<p><br>


Roles
----------------
<p>
Los roles siguen una estructura de directorios definida; un role es nombrado por el directorio de nivel superior. 
Algunos de los subdirectorios contienen archivos YAML, denominados main.yml. 
Los subdirectorios de archivos y plantillas pueden contener objetos a los que hacen referencia los archivos YAML.

Una estructura de proyecto podría tener este aspecto.
<pre>
OcpNodos/
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── README.md
├── tasks
│   └── main.yml
├── templates
├── tests
│   ├── inventory
│   └── test.yml
└── vars
    └── main.yml
</pre>

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).



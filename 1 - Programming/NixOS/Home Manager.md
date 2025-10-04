04/10/2025
Tags: #Nix #NixOS #Flakes 
Lenguaje Programación: #Nix 

# Home Manager
Hay dos formas de instalar home manager la primera: Standalone esta es la mas "portable" porque podemos tenerla en otra maquina en la cual no tengamos permisos de root, esto se da sino estoy mal porque separa la carpeta user config de system config. En cambio NixOS module necesitamos permisos de root porque user config esta al mismo nivel que system config 

Para instalar Home-Manager debemos seguir los siguientes pasos que se encuentran en el link [Home manager manual](https://nix-community.github.io/home-manager/index.xhtml#sec-install-standalone): Después de terminar el paso 3 podemos abrir la carpeta

```bash
cd .config/home-manager 

sudo nvim home.nix
# Instalamos el paquete hello
# Para hacer un switch del home manager usamos el comando 
home-manager switch
```


Para volver a una generación de home-manager especifica debemos ejecutar 

```bash
home-manager generations
# Aqui se mostraran las generaciones y los simlinks 
# Nosotros copiamos el simlink de la generacion que querramos y damos /activate

/nix/store/....-home-manager-generation/activate
```


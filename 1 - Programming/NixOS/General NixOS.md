30/09/2025
Tags: #NixOS #Flakes #Nix 
Lenguaje Programación: 

# General NixOS

# Nix
Nix es un gestor de paquetes declarativo, permite a los usuarios declarar el estado de configuración deseado del sistema. Todo esto en archivos de configuración. La ventaja de un gestor de paquetes declarativo es que solo necesitamos indicar que deseamos reemplazar cierto paquete. Por ejemplo, si deseamos usar Spotify en NixOS, solo necesitamos ir a la ruta: `/etc/nixos` después de esto hacer cambios en el documento `configuration.nix` y ahí indicar los paquetes que queremos. Estos paquetes pueden ser buscados en [NixOS Search - Packages - hyprland](https://search.nixos.org/packages?channel=25.05&query=hyprland)

Es importante saber que un sistema operativo consta de varios paquetes de software, archivos de configuración, etc, etc. Que representan el estado actual del sistema la configuración declarativa solo puede gestionar la parte estática de este estado. Los datos dinámicos, como los de PostgreSQL, MySQL, etc. No se pueden gestionar de forma eficaz mediante la configuración declarativa. 

Otra de las grandes ventajas que nos presenta NixOS es que podemos revertir el sistema a cualquier estado anterior. 


# Ventajas NixOS


# Cosas que no entiendo 
Principalmente son los flakes. No comprendo absolutamente nada que son los flakes, por lo que tengo entendido estos mejoran la reproducibilidad del sistema, en los archivos flake.lock se registran las direcciones de las fuentes de datos, los valores hash y otra información relevante para todas las dependencias. 

# Desventajas de NixOS
Para lograr tener una reproducibilidad completa, es necesario conocer todo el diseño de Nix y gestionar el sistema de forma declarativa en lugar de usar nix-env-i

Nix flakes sigue siendo una función experimental y hay poca documentación especifica sobre ella, el método mas sencillo y mas documentado es `/etc/nixos` `configuration.nix` Para lograr aprender Nix Flakes se debe consultar una cantidad significativa de documentación. Además, algunas características básicas de Nix, como las importaciones y el sistema de módulos Nixpkgs, carecen de documentación oficial detallada, lo que obliga a recurrir al análisis del código fuente

Aun no entiendo porque hay dos formas de instalación de programas en NixOS. Primero tenemos `programs.nombrePrograma.enable = true` esto lo que hace es habilitar la aplicación como un modulo ademas de instalarla y configurar un modulo en los cuales se pueden configurar variables de entorno, servicios, plugins, atajos, etc. Y tenemos `environment.systemPackages = with pkgs; [programa];` esto lo que hace es descargar el binario y dejar el programa disponible para todos los usuarios, es la forma genérica sin embargo no configura servicios ni extras.

Para saber si se tiene que usar un modulo lo recomendando es buscar en [Nix Packages](https://search.nixos.org/options?channel=25.05&query=firefox) si el programa tiene `programs.<nombre>.enable` hay que usarlo como modulo, y si no hay esa etiqueta se usa como package.

# Configurando gráfica Nvidia y sus drivers
Configurar estos gráficos esta siendo mas sencillo de lo esperado, debido a que solamente tenemos que editar el archivo `configuration.nix` y hay una [NixOS Wiki](https://wiki.nixos.org/wiki/NVIDIA#Footnotes) muy buena de la cual me estoy auxiliando.

Es importante también configurar el PRIME que por lo que entiendo sirve para escoger si los procesos se realizaran con la iGPU (Integrated GPU) o la dGPU (Dedicated GPU) hay dos formas de configurarlo el "Common Setup" y el Offload Mode

Después de haber ajustado ciertas configuraciones como 

```Nix
hardware.graphic.enable = true;
services.xserver.videoDrivers = [ "nvidia" ];
hardware.nvidia.open = false; # Esto es super importante
```

Al momento de haber puesto hardware open en false todo se soluciono, con el open source habíap tenido un error de compilación. Sin embargo el propietario me funciono perfectamente 

Para comprobar si los drivers de la gráfica y como tal la gráfica es reconocida y es usable por el sistema podemos utilizar lo siguiente: 

```Bash
# Primero debemos instalar mesa-demo que es un paquete que nos permite usar glxgears 

cd/etc/nixos
sudo nvim configuration.nix
# Instalamos mesa-models

sudo nixos-rebuild switch 
reboot

nvidia-smi 
# Aqui revisamos cuandos mb esta consumiendo la grafica 

nvidia-offload glxgears
# En simultaneo que se esta ejecutando glxgears podemos abrir una terminal nueva y aqui revisar los recursos de nvidia con nvidia-smi
```

Para saber que canal de NixOs estamos utilizando debemos ejecutar el siguiente comando como root:
`nix-channel --list | grep nixos`


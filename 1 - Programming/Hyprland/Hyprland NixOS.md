15/10/2025
Tags: #Hyprland #Waybar #Wofi 
Lenguaje Programación: 

# Hyprland NixOS

# Instalación
Como tal el tema de instalación no fue nada complicado, únicamente tuvimos que editar el archivo `configuration,nix` en la ruta `~/.dotfiles/configuration,nix` dentro de este archivo tenemos que indicar ciertos parámetros nuevos tenemos que activar un modulo hyprland después instalamos los paquetes necesarios para hyprland. 

Después de esto viene el tema de la configuración

# Configuración 

Para editar hyprland y sus asociados tenemos que ir a la ruta: `~/.config/` aquí vamos a encontrar los directorios hypr, waybar, etc. 

Las cosas mas importantes a modificar de hyprland diría que son: 
<ol>
	<li>Modificar la escala de monitores</li>
	<li>Modificar la terminal para que usemos ghostty en lugar de kitty</li>
	<li>Modificar para que hyprland ejecute siempre sww y el bash script que tenemos para settear los fondos</li>
	<li>Activar waybar para que se ejecute siempre que se inicie hyprland</li>
</ol>




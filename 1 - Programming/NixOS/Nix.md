17/10/2025
Tags: 
Lenguaje Programación: 

# Nix

Nix es un sistema de gestion de paquetes, todos los paquetes y configuraciones se describen como funciones puras, nada se instala "globalmente" sino que cada version de un paquete vive en su propio espacio `/nix/store` En lugar de modificar nuestro sistema nix lo que hace es construir hashes que representan el resultado exacto de una expresion de Nix  
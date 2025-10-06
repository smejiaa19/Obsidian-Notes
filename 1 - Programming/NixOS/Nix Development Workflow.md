05/10/2025
Tags: #Nix #NixOS #Java #Python
Lenguaje Programación: 

# Nix Development Workflow
Dev shells son una herramienta muy interesante en Nix, las Dev Shells nos permiten entrar en un entorno en el que tenemos todas las dependencias de desarrollo, esto sin alterar el sistema host. 

Es decir: 
<ol>
	<li>Cada proyecto esta completamente aislado de los demás, sin mas dependencias entre ellos.</li>
	<li>Los paquetes no contaminan el gráfico de dependencias del sistema y los paquetes solo son visibles dentro del shell</li>
</ol>
Para compartir un shell de desarrollo es fácil, solo hay que descargar los archivos nixfiles en el repo y todo el mundo estará a un shell de Nix de obtener todos los requisitos para compilar o utilizar el proyecto 

Cuando salimos del shell todo desaparece y nuestro sistema queda limpito. 

Es importante saber o por lo que entiendo que basicamente no es que los paquetes se eliminen cuando nos vamos de la shell, sino que quedan en el directorio /store ahi como orfanatos. Por otro lado la nix-shell lo que hara es basicamente abrir una terminal como su nombre indica. De ahi nosotros debemos abrir pycharm o intellij idea para exponer los paquetes y dependencias que estemos usando en este projecto. 

Para abrir pycharm y idea: 
```bash
# Pycharm
nvidia-offload pycharm-professional &

#IntellijIdea
nvidia-offload idea-ultimate &
```


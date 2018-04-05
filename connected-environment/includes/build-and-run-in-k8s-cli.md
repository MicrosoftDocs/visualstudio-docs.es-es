## <a name="build-and-run-code-in-kubernetes"></a>Compilar y ejecutar código en Kubernetes
Vamos a ejecutar nuestro código. En la ventana de terminal, ejecute este comando desde la **carpeta de código raíz**, webfrontend:

```cmd
vsce up
```

Fíjese en la salida del comando, verá varias cosas a medida que la tarea va avanzando:
1. El código fuente se sincroniza con el entorno de desarrollo en Azure.
1. Se crea una imagen de contenedor en Azure, según lo especificado por los activos de Docker en la carpeta de código.
1. Se crean objetos de Kubernetes que usan la imagen del contenedor, según lo especificado por el gráfico de Helm en la carpeta de código.
1. Se muestra información sobre los puntos de conexión del contenedor. En nuestro caso, esperamos ver una dirección URL HTTPS pública.
1. Suponiendo que las fases anteriores finalizan correctamente, debería empezar a ver la salida `stdout` (y `stderr`) a medida que el contenedor se inicia.

> [!Note]
> Estos pasos tardarán más tiempo la primera vez el comando `up` se ejecute, pero las siguientes veces serán más rápidos.

## <a name="test-the-web-app"></a>Probar la aplicación web
Estudie la salida de la consola para obtener información sobre la dirección URL pública que creó el comando `up`. Tendrá la siguiente forma: 

`Running at public URL: https://<servicename>-<environmentname>.vsce.io` 

Abra esta dirección URL en una ventana del explorador; debería ver que la aplicación web se carga. Mientras el contenedor se ejecuta, la salida `stdout` y `stderr` se transmite a la ventana de terminal.

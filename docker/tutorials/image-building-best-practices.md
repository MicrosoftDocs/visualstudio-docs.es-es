---
title: 'Tutorial de Docker - Parte 8: Capas de imágenes'
description: Procedimiento para examinar y administrar capas de imagen en imágenes de Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "89176819"
---
# <a name="image-layering"></a>Capas de imágenes

¿Sabía que puede ver lo que conforma una imagen? Con el comando `docker image history`, puede ver el comando que se ha usado para crear cada capa dentro de una imagen.

1. Use el comando `docker image history` para ver las capas de la imagen `getting-started` que ha creado antes en el tutorial.

    ```bash
    docker image history getting-started
    ```

    Debería obtener una salida similar a la siguiente (las fechas y los identificadores pueden ser diferentes).

    ```plaintext
    IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
    a78a40cbf866        18 seconds ago      /bin/sh -c #(nop)  CMD ["node" "/app/src/ind…   0B                  
    f1d1808565d6        19 seconds ago      /bin/sh -c yarn install --production            85.4MB              
    a2c054d14948        36 seconds ago      /bin/sh -c #(nop) COPY dir:5dc710ad87c789593…   198kB               
    9577ae713121        37 seconds ago      /bin/sh -c #(nop) WORKDIR /app                  0B                  
    b95baba1cfdb        13 days ago         /bin/sh -c #(nop)  CMD ["node"]                 0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  ENTRYPOINT ["docker-entry…   0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) COPY file:238737301d473041…   116B                
    <missing>           13 days ago         /bin/sh -c apk add --no-cache --virtual .bui…   5.35MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV YARN_VERSION=1.21.1      0B                  
    <missing>           13 days ago         /bin/sh -c addgroup -g 1000 node     && addu…   74.3MB              
    <missing>           13 days ago         /bin/sh -c #(nop)  ENV NODE_VERSION=12.14.1     0B                  
    <missing>           13 days ago         /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B                  
    <missing>           13 days ago         /bin/sh -c #(nop) ADD file:e69d441d729412d24…   5.59MB   
    ```

    Cada una de las líneas representa una capa en la imagen. En esta pantalla se muestra la base en la parte inferior y la capa más reciente en la parte superior. Con esto, también puede ver rápidamente el tamaño de cada capa, lo que ayuda a diagnosticar imágenes grandes.

1. Observará que algunas de las líneas se truncan. Si agrega la marca `--no-trunc`, obtendrá la salida completa (sí, se usa una marca truncada para obtener una salida no truncada).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Almacenamiento en caché de capas

Ahora que ha visto las capas en funcionamiento, debe aprender algo importante para reducir los tiempos de compilación de las imágenes de contenedor.

> Después de que cambie una capa, también se deben volver a crear todas las capas inferiores

Volverá a examinar el Dockerfile que ha usado antes.

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

De nuevo en la salida del historial de imágenes, verá que cada comando del Dockerfile se convierte en una nueva capa de la imagen. Es posible que recuerde que cuando realizó un cambio en la imagen, tuvo que volver a instalar las dependencias de Yarn. ¿Hay alguna manera de solucionar esto? No tiene mucho sentido enviar las mismas dependencias cada vez que se compila, ¿verdad?

Para solucionarlo, puede reestructurar el Dockerfile para que se admita el almacenamiento en caché de las dependencias. En el caso de las aplicaciones basadas en Node, esas dependencias se definen en el archivo `package.json`. Por tanto, ¿qué ocurre si primero solo copia ese archivo, instala las dependencias y *después* copia todo lo demás? Luego, solo tiene que volver a crear las dependencias de Yarn si se ha producido un cambio en `package.json`. ¿Tiene sentido?

1. Actualice el Dockerfile para copiar primero `package.json`, instale las dependencias y, después, copie todo lo demás.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Compile una nueva imagen mediante `docker build`.

    ```bash
    docker build -t getting-started .
    ```

    Debería ver una salida como esta...

    ```plaintext
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Running in d53a06c9e4c2
    yarn install v1.17.3
    [1/4] Resolving packages...
    [2/4] Fetching packages...
    info fsevents@1.2.9: The platform "linux" is incompatible with this module.
    info "fsevents@1.2.9" is an optional dependency and failed compatibility check. Excluding it from installation.
    [3/4] Linking dependencies...
    [4/4] Building fresh packages...
    Done in 10.89s.
    Removing intermediate container d53a06c9e4c2
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> a239a11f68d8
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 49999f68df8f
    Removing intermediate container 49999f68df8f
    ---> e709c03bc597
    Successfully built e709c03bc597
    Successfully tagged getting-started:latest
    ```

    Verá que todas las capas se han vuelto a generar. Todo correcto, porque ha modificado considerablemente el Dockerfile.

1. Ahora, realice un cambio en el archivo `src/static/index.html` (por ejemplo, cambie `<title>` para que indique "The Awesome Todo App").

1. Vuelva a compilar la imagen de Docker, ahora con `docker build`. Esta vez, la salida debe tener un aspecto ligeramente diferente.

    ```plaintext hl_lines="5 8 11"
    Sending build context to Docker daemon  219.1kB
    Step 1/6 : FROM node:12-alpine
    ---> b0dc3a5e5e9e
    Step 2/6 : WORKDIR /app
    ---> Using cache
    ---> 9577ae713121
    Step 3/6 : COPY package* yarn.lock ./
    ---> Using cache
    ---> bd5306f49fc8
    Step 4/6 : RUN yarn install --production
    ---> Using cache
    ---> 4e68fbc2d704
    Step 5/6 : COPY . .
    ---> cccde25a3d9a
    Step 6/6 : CMD ["node", "/app/src/index.js"]
    ---> Running in 2be75662c150
    Removing intermediate container 2be75662c150
    ---> 458e5c6f080c
    Successfully built 458e5c6f080c
    Successfully tagged getting-started:latest
    ```

    En primer lugar, debe tener en cuenta que la compilación ha sido mucho más rápida. Además, verá que todos los pasos 1-4 tienen `Using cache`. Enhorabuena. Usa la caché de compilación. La inserción y extracción de esta imagen (y su actualización) también serán mucho más rápidas. Enhorabuena.

## <a name="multi-stage-builds"></a>Compilaciones de varias fases

Aunque en este tutorial no se va a profundizar demasiado en este concepto, las compilaciones en varias fases son una herramienta increíblemente eficaz que ayuda a usar varias fases para crear una imagen. Ofrecen varias ventajas:

- Dependencias de tiempo de compilación independientes de las dependencias en tiempo de ejecución
- Reducción del tamaño total de la imagen mediante el envío *exclusivo* de lo que la aplicación necesita para ejecutarse.

### <a name="maventomcat-example"></a>Ejemplo de Maven/Tomcat

Al compilar aplicaciones basadas en Java, se necesita un JDK para compilar el código fuente en código de bytes de Java. Pero ese JDK no es necesario en producción. Además, es posible que use herramientas como Maven o Gradle para compilar la aplicación.
Tampoco son necesarias en la imagen final. La ayuda proviene de las compilaciones de varias fases.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

En este ejemplo se usa una fase (llamada `build`) para realizar la compilación real de Java mediante Maven. La segunda fase (a partir de `FROM tomcat`) copia los archivos de la fase `build`. La imagen final es solo la última fase que se va a crear (que se puede invalidar con la marca `--target`).

### <a name="react-example"></a>Ejemplo de React

Al compilar aplicaciones de React, se necesita un entorno de Node para compilar el código de JS (normalmente, JSX), hojas de estilos de SASS y mucho más en HTML, JS y CSS estático. Si no va a realizar la representación del lado servidor, ni siquiera necesita un entorno de Node para la compilación de producción. ¿Por qué no enviar los recursos estáticos en un contenedor nginx estático?

```dockerfile
FROM node:12 AS build
WORKDIR /app
COPY package* yarn.lock ./
RUN yarn install
COPY public ./public
COPY src ./src
RUN yarn run build

FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
```

Aquí se usa una imagen de `node:12` para realizar la compilación (y maximizar el almacenamiento en caché de las capas) y, después, copiar la salida en un contenedor nginx. Genial, ¿verdad?

## <a name="recap"></a>Resumen

Al comprender un poco más la estructura de las imágenes, puede crearlas más rápidamente y enviar menos cambios. Las compilaciones de varias fases también ayudan a reducir el tamaño total de la imagen y a aumentar la seguridad de los contenedores mediante la separación de las dependencias en tiempo de compilación de las dependencias en tiempo de ejecución.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Implementación en la nube](deploy-to-cloud.md)
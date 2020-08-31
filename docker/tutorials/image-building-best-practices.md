---
title: 'Tutorial de Docker, parte 8: capas de imágenes'
description: Cómo examinar y administrar las capas de imagen en las imágenes de Docker.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: eae21a729f30a0c77fa52e5774a2f5157286dab1
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176819"
---
# <a name="image-layering"></a>Capas de imágenes

¿Sabía que puede ver lo que conforma una imagen? Con el `docker image history` comando, puede ver el comando que se usó para crear cada capa dentro de una imagen.

1. Use el `docker image history` comando para ver las capas de la `getting-started` imagen que creó anteriormente en el tutorial.

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

    Cada una de las líneas representa una capa en la imagen. En la pantalla siguiente se muestra la base en la parte inferior con la capa más reciente en la parte superior. Con esto, también puede ver rápidamente el tamaño de cada capa, lo que ayuda a diagnosticar imágenes grandes.

1. Observará que algunas de las líneas se truncan. Si agrega la `--no-trunc` marca, obtendrá la salida completa (sí, se usa una marca truncada para obtener la salida no truncada).

    ```bash
    docker image history --no-trunc getting-started
    ```

## <a name="layer-caching"></a>Almacenamiento en caché de capas

Ahora que ha visto el nivel de acción, hay una lección importante para aprender a reducir los tiempos de compilación de las imágenes de contenedor.

> Una vez que una capa cambia, también se deben volver a crear todas las capas inferiores

Echemos un vistazo a la Dockerfile que estaba usando una vez más...

```dockerfile
FROM node:12-alpine
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "/app/src/index.js"]
```

Volviendo a la salida del historial de imágenes, verá que cada comando de Dockerfile se convierte en una nueva capa de la imagen. Es posible que recuerde que cuando realizó un cambio en la imagen, las dependencias de los hilados tenían que volver a instalarse. ¿Hay alguna manera de solucionar esto? No tiene mucho sentido enviar las mismas dependencias cada vez que compila, ¿bien?

Para solucionarlo, puede reestructurar el Dockerfile para ayudar al almacenamiento en caché de las dependencias. En el caso de las aplicaciones basadas en nodos, dichas dependencias se definen en el `package.json` archivo. Por lo tanto, ¿qué ocurre si solo copió ese archivo en primer lugar, instala las dependencias y *después* copia en todo lo demás? A continuación, solo vuelve a crear las dependencias de hilados si se produjo un cambio en `package.json` . ¿Tiene sentido?

1. Actualice el Dockerfile para copiarlo en el `package.json` primero, instale las dependencias y, a continuación, copie todo lo demás en.

    ```dockerfile hl_lines="3 4 5"
    FROM node:12-alpine
    WORKDIR /app
    COPY package.json yarn.lock ./
    RUN yarn install --production
    COPY . .
    CMD ["node", "/app/src/index.js"]
    ```

1. Cree una nueva imagen mediante `docker build` .

    ```bash
    docker build -t getting-started .
    ```

    Debería ver un resultado similar al siguiente...

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

    Verá que todas las capas se han vuelto a generar. Perfectamente bien, dado que cambió el Dockerfile bastante.

1. Ahora, realice un cambio en el `src/static/index.html` archivo (por ejemplo, cambie el `<title>` para decir "la aplicación maravilla todo").

1. Compilar la imagen de Docker ahora con el uso de `docker build` nuevo. Esta vez, la salida debe tener un aspecto ligeramente diferente.

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

    En primer lugar, debe tener en cuenta que la compilación fue mucho más rápida. Además, verá que todos los pasos del 1-4 `Using cache` . Por lo tanto, alegría! Está usando la memoria caché de compilación. Insertar y extraer esta imagen y actualizarla también será mucho más rápido. Alegría!

## <a name="multi-stage-builds"></a>Compilaciones de varias fases

Aunque no vamos a profundizar en él demasiado en este tutorial, las compilaciones en varias fases son una herramienta increíblemente eficaz que ayuda a usar varias fases para crear una imagen. Hay varias ventajas para ello:

- Dependencias de tiempo de compilación independientes de las dependencias en tiempo de ejecución
- Reducir el tamaño total de la imagen enviando *solo* lo que la aplicación necesita para ejecutarse

### <a name="maventomcat-example"></a>Ejemplo de Maven/Tomcat

Al compilar aplicaciones basadas en Java, se necesita un JDK para compilar el código fuente en el código de bytes de Java. Sin embargo, ese JDK no es necesario en producción. Además, es posible que use herramientas como Maven o Gradle para ayudar a compilar la aplicación.
Estos tampoco son necesarios en la imagen final. Ayuda para las compilaciones en varias fases.

```dockerfile
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps 
```

En este ejemplo se usa una fase (denominada `build` ) para realizar la compilación real de Java con Maven. La segunda fase (a partir de `FROM tomcat` ) copia los archivos de la `build` fase. La imagen final es solo la última fase que se crea (que se puede invalidar mediante la `--target` marca).

### <a name="react-example"></a>Ejemplo de reAct

Al compilar aplicaciones de reAct, necesita un entorno de nodo para compilar el código de JS (normalmente, JSX), hojas de estilos de SASS y mucho más en HTML, JS y CSS estático. Si no está realizando la representación del lado servidor, ni siquiera necesita un entorno de nodo para la compilación de producción. ¿Por qué no enviar los recursos estáticos en un contenedor nginx estático?

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

Aquí se usa una `node:12` imagen para realizar la compilación (maximizando el almacenamiento en caché de capas) y luego copiar la salida en un contenedor nginx. Genial, ¿verdad?

## <a name="recap"></a>Resumen

Al comprender un poco más sobre cómo se estructuran las imágenes, puede crear imágenes más rápido y enviar menos cambios. Las compilaciones de varias fases también ayudan a reducir el tamaño total de la imagen y a aumentar la seguridad de los contenedores mediante la separación de las dependencias en tiempo de compilación de las dependencias del tiempo de ejecución.

## <a name="next-steps"></a>Pasos siguientes

Continúe con el tutorial.

> [!div class="nextstepaction"]
> [Implementación en la nube](deploy-to-cloud.md)
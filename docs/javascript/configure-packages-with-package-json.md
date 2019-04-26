---
title: Configurar los paquetes de npm con package.json
description: Especifique las versiones del paquete de npm mediante package.json
ms.date: 09/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: eb0267f668121e4d56f113798b14810f3446b8cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960613"
---
# <a name="packagejson-configuration"></a>Configuración de package.json

Si está desarrollando una aplicación de Node.js con muchos paquetes de npm, no es raro que aparezcan advertencias o errores al compilar el proyecto si se han actualizado uno o varios paquetes. En ocasiones, se produce un conflicto de versiones o una versión del paquete se encuentra en desuso. Estas son algunas sugerencias rápidas para ayudarle a configurar su archivo [package.json](https://docs.npmjs.com/files/package.json) y comprender qué sucede cuando ve advertencias o errores. Esta no es una guía completa de *package.json* y se centra solo en las versiones de paquetes de npm.

El sistema de control de versiones de paquetes de npm tiene reglas estrictas. El formato de las versiones es el siguiente:

    [major].[minor].[patch]

Supongamos que tiene un paquete en la aplicación con la versión 5.2.1. La versión principal es 5, la versión secundaria es 2 y el parche es 1.

* En una actualización de versión principal, el paquete incluye nuevas características que no son compatibles con versiones anteriores, es decir, cambios importantes.
* En una actualización de versión secundaria, se han agregado nuevas características al paquete que son compatibles con versiones anteriores del paquete.
* En una actualización de revisión, se incluyen una o varias correcciones de errores. Las correcciones de errores son siempre compatibles con versiones anteriores.

Conviene tener en cuenta que algunas características del paquete de npm tienen dependencias. Por ejemplo, para usar una nueva característica del paquete de compilador de TypeScript (ts-loader) con webpack, es posible que también tenga que actualizar los paquetes webpack npm y webpack-cli.

Para ayudar a administrar el control de versiones del paquete, npm es compatible con varias notaciones que puede usar en el archivo *package.json*. Puede usar estas notaciones para controlar el tipo de actualizaciones del paquete que quiere aceptar en la aplicación.

Supongamos que está usando React y debe incluir los paquetes npm **react** y **react-dom**. Podría especificarlo de varias maneras en su archivo *package.json*. Por ejemplo, puede especificar el uso de la versión exacta de un paquete de la siguiente forma.

  ```json
  "dependencies": {
    "react": "16.4.2",
    "react-dom": "16.4.2",
  },
  ```

Al usar la notación anterior, npm siempre obtendrá la versión exacta especificada, 16.4.2.

Puede usar una notación especial para limitar las actualizaciones a solo actualizaciones de revisiones (correcciones de errores). En este ejemplo:

  ```json
  "dependencies": {
    "react": "~16.4.2",
    "react-dom": "~16.4.2",
  },
  ```

se usa el carácter de tilde (~) para indicar a npm que solo actualice un paquete cuando sea una revisión. Por lo tanto, npm puede actualizar react 16.4.2 a 16.4.3 (o 16.4.4, etc.), pero no aceptará una actualización de la versión principal o secundaria. Por lo tanto, no se actualizará 16.4.2 a 16.5.0.

También puede usar el símbolo de intercalación (^) para especificar que npm puede actualizar el número de versión secundaria.

  ```json
  "dependencies": {
    "react": "^16.4.2",
    "react-dom": "^16.4.2",
  },
  ```

Al usar esta notación, npm puede actualizar react 16.4.2 a 16.5.0 (o 16.5.1, 16.6.0, etc.), pero no aceptará una actualización de la versión principal. Por lo tanto, no se actualizará 16.4.2 a 17.0.0.

Cuando npm actualiza los paquetes, genera un archivo *package-lock.json*, que enumera las versiones del paquete de npm reales usadas en la aplicación, incluidos todos los paquetes anidados. Aunque *package.json* controla las dependencias directas de la aplicación, no controla las dependencias anidadas (otros paquetes de npm requeridos por un paquete de npm determinado). Puede usar el archivo *package-lock.json* en el ciclo de desarrollo si necesita asegurarse de que otros desarrolladores y evaluadores usan los paquetes exactos que está usando, incluidos los paquetes anidados. Para obtener más información, consulte [package-lock.json](https://docs.npmjs.com/files/package-lock.json) en la documentación de npm.

Para Visual Studio, el archivo *package-lock.json* no se agrega al proyecto, pero se puede encontrar en la carpeta del proyecto.

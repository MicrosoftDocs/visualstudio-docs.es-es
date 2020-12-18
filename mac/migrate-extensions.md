---
title: 'Solución del problema: ¿Cómo publico una nueva versión de mi extensión existente?'
description: Guía para actualizar extensiones a través del flujo de trabajo de publicación.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488548"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Solución del problema: ¿Cómo publico una nueva versión de mi extensión existente?

> [!IMPORTANT]
> Actualmente, la creación de nuevas extensiones no se admite oficialmente en Visual Studio 2019 para Mac.

El servidor del repositorio de extensiones de Visual Studio para Mac se moverá el 15 de enero de 2021. Este cambio no afectará a los usuarios que ya han descargado la extensión, pero cambiará la forma de publicar nuevas versiones de la extensión después de esa fecha.

Como autor de una extensión actual, deberá seguir un flujo de trabajo diferente para publicar las próximas actualizaciones. Este proceso consta de las siguientes secciones:
- Configuración de un repositorio público de GitHub para cada extensión.
- Compartir la dirección URL del repositorio con el equipo de Visual Studio para Mac a través de la [lista de distribución de correo para la publicación de extensiones](mailto:vsmextpub@microsoft.com).
- Actualización de la extensión con la característica de versiones en GitHub.


## <a name="initial-setup"></a>Instalación inicial 

Para seguir publicando actualizaciones de las extensiones, deberá crear un repositorio de GitHub público. Si publica varias extensiones, deberá tener un repositorio aparte para cada una, a menos que siempre cree las versiones y las publique juntas, en cuyo caso puede usar un solo repositorio.

> [!NOTE]
> Aunque el repositorio de GitHub para la extensión debe ser público, no es necesario que hospede ahí ningún código. Para seguir este proceso, no es necesario que tenga ningún código en GitHub.


## <a name="share-the-location-of-your-repository"></a>Compartir la ubicación del repositorio

Una vez que haya configurado el repositorio, envíe un correo electrónico a la [lista de distribución de correo para la publicación de extensiones](mailto:vsmextpub@microsoft.com) con la dirección URL.


## <a name="release-a-new-version"></a>Lanzamiento de una nueva versión

Utilice el vínculo "Crear una nueva versión" de la página principal del repositorio para comenzar el proceso de actualización de la extensión. Una vez que haya seleccionado ese vínculo, siga estos pasos:

1. Agregue información a la **etiqueta de versión** con el formato siguiente:

    > v\<releaseVersion>\-vsm\<targetVersion>

    Donde:
     - **&lt;releaseVersion&gt;** es el número de versión de la extensión.
     - **&lt;targetVersion&gt;** es la versión mínima de Visual Studio para Mac a la que va dirigida la extensión.

2. (Opcional) Los campos del **título** y la **descripción** se pueden rellenar con cualquier información que desee. Este flujo de trabajo no usa la información de esos campos.

3. Asegúrese de que la casilla de **versión preliminar** esté desactivada. Si está activada, el proceso de publicación no recogerá la versión.

4. Adjunte los archivos **.mpack** que implementan la extensión en la sección de **archivos binarios**. Se pueden adjuntar varios archivos **.mpack** en una versión.

Visual Studio para Mac mostrará la versión más reciente de la extensión que sea compatible con la instalación de Visual Studio para Mac que se usó para acceder al repositorio de la extensión.

Si ha registrado el repositorio de GitHub en el equipo de Visual Studio para Mac, Visual Studio para Mac tomará la versión de la extensión en un plazo de 24 horas.

## <a name="additional-information"></a>Información adicional

- Las versiones que no cumplan los requisitos que aquí se indican no se publicarán. 
- Después del 15 de enero de 2021, las actualizaciones de extensiones solo se mostrarán en Visual Studio para Mac 8.0 o posterior.
- Las extensiones actuales seguirán estando disponibles para los usuarios de Visual Studio para Mac sin necesidad de que hagan nada. Solo tiene que seguir las instrucciones de esta guía si publica una nueva versión después del 15 de enero de 2021.

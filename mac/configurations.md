---
title: Descripción de las configuraciones de compilación
description: Este artículo describe las diversas configuraciones de compilación en Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/18/2019
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 911d8d3a65c414bc3c98494bda75c46b778e5b2b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584027"
---
# <a name="understanding-build-configurations"></a>Descripción de las configuraciones de compilación

Se pueden almacenar diferentes configuraciones de propiedades de solución y de proyecto para usar en distintos tipos de compilaciones durante el proceso de desarrollo. Los proyectos que se crean con Visual Studio para Mac mediante una plantilla suelen incluir configuraciones de depuración y lanzamiento que admiten la depuración y la implementación de una aplicación, respectivamente. 

Si quiere crear configuraciones personalizadas, consulte [Creación y edición de configuraciones de compilación](./create-and-edit-configurations.md).

>[!NOTE]
>Este tema se aplica a Visual Studio para Mac. Para Visual Studio en Windows, consulte [Descripción de las configuraciones de compilación](/visualstudio/ide/understanding-build-configurations).

## <a name="solution-configurations"></a>Configuraciones de solución

Las configuraciones de solución se usan para especificar configuraciones para todos los proyectos de una solución. Con la pestaña **Asignaciones de configuración** del elemento **Compilar > Configuraciones**, puede asignar una configuración de destino para cada elemento de la solución abierta. Esto último se muestra en la imagen siguiente:

![Opciones de asignación de configuración](media/projects-and-solutions-image3.png)

Para obtener más información sobre configuraciones, vea el vídeo [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) (Administrador de configuración) de James Montemagno.

## <a name="project-build-configurations"></a>Configuraciones de compilación del proyecto

Los proyectos suelen tener varias configuraciones. La configuración y la plataforma de destino de proyecto se usan conjuntamente para especificar las propiedades que se van a usar al compilarlo. Se puede tener diferentes salidas en tiempo de compilación si se cambia entre las configuraciones. Por ejemplo, una configuración de depuración tendrá como resultado símbolos de depuración, lo que permite al depurador resolver nombres de función, parámetros o variables del seguimiento de la pila de una aplicación bloqueada. Aunque esta información adicional es útil durante el desarrollo, conduce a un tamaño de archivo excesivo y no es ideal para la distribución.

Cada plataforma tiene configuraciones específicas para su compilación. Se puede tener acceso a las páginas de configuración de compilación de los proyectos desde la sección **Compilación** del cuadro de diálogo **Opciones del proyecto**. Para abrir este cuadro de diálogo, haga clic con el botón derecho en el proyecto y seleccione **Opciones**, o bien haga doble clic en el proyecto en el explorador de soluciones.

## <a name="run-configuration"></a>Configuración de ejecución

Visual Studio para Mac le permite establecer una _configuración de ejecución_. Las configuraciones de ejecución se presentan en una lista desplegable de la barra de herramientas, junto al selector de la configuración de compilación, como se muestra a continuación:

![Desplegable de configuración de ejecución](media/projects-and-solutions-image8.png)

Una configuración de ejecución es un conjunto de opciones de ejecución con un nombre y varias configuraciones que se definen en un proyecto para diferentes fines. Las configuraciones de ejecución se definen en el nivel de proyecto, y para cada proyecto ejecutable se crea automáticamente una predeterminada, aunque es posible agregar tantas como sea necesario. Determinados tipos de proyecto generan automáticamente configuraciones de ejecución adicionales. Por ejemplo, los proyectos de watchOS pueden generar _configuraciones de vista rápida y notificación_.

Las configuraciones se pueden compartir con otros desarrolladores (en cuyo caso se almacenarán en el archivo .csproj) o conservarse localmente (en cuyo caso se almacenarán en un archivo .user).

### <a name="android-run-configurations"></a>Configuraciones de ejecución de Android

Las configuraciones de ejecución para proyectos de Android permiten especificar qué actividad, servicio o receptor de difusión iniciar al ejecutar o depurar el proyecto. Puede pasar datos adicionales de intención y establecer marcas de intención para probar los componentes con diferentes condiciones de inicio.

Aquellas actividades distintas a `MainLauncher` deberán tener `Exported=true` agregado al atributo Actividad para la depuración en un dispositivo físico o tener filtros de intención definidos.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Ejemplos de datos que se podrían incluir en configuraciones de ejecución

En la siguiente lista se proporcionan algunos ejemplos de datos que se podrían incluir en configuraciones de ejecución:

* Proyecto de .NET normal
  * Aplicación de inicio alternativa
  * Argumentos de inicio
  * Directorio de trabajo
  * Variables de entorno
  * Opciones del entorno de ejecución Mono (para usarse solo al ejecutar en Mono)
* Proyecto de Android
  * Punto de entrada (actividad, servicio, receptor)
  * Datos y argumentos de intención
* Proyecto de iOS
  * Modo (Normal, Recuperación de cambios)
* Proyecto de extensión de iOS
  * Aplicación de inicio: predeterminada o personalizada
* Proyecto de WatchKit
  * Modo (Vista rápida, Notificación)
  * Carga de notificaciones

## <a name="see-also"></a>Vea también

- [Descripción de las configuraciones de compilación (Visual Studio en Windows)](/visualstudio/ide/understanding-build-configurations)
---
title: Opciones de configuración del proyecto C++
description: Obtenga información sobre cómo usar la página Configuración del proyecto de VC++ de la sección Proyectos y soluciones para definir la configuración de compilación y del proyecto de C++ relacionada con el registro, el rendimiento y los tipos de archivos compatibles.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 16226cd66c2cf46d1dc46f1cb3f90dc3bad9658c
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616283"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Configuración de proyecto de VC++, Proyectos y soluciones, Opciones (Cuadro de diálogo)

Este cuadro de diálogo le permite definir la configuración del proyecto y la compilación de C++ relacionada con el registro, el rendimiento y los tipos de archivos auxiliares.

## <a name="to-access-this-dialog-box"></a>Para obtener acceso a este cuadro de diálogo

1. En el menú **Herramientas** , haga clic en **Opciones**.

2. Seleccione **Proyectos y soluciones** y **Configuración de proyecto de VC++**.

## <a name="build-logging"></a>Registro de compilación

 **Sí**

  Habilita la generación del archivo de registro de compilación. Esta opción genera BuildLog.htm, que se encuentra en el directorio de archivos intermedios del proyecto. Cada compilación nueva sobrescribe el archivo BuildLog.htm anterior.

 **No**

  Desactiva la generación del archivo de registro de compilación.

## <a name="show-environment-in-log"></a>Mostrar entorno en el registro

 **Sí**

Muestra las variables de entorno en el archivo de registro de compilación. Esta opción especifica que se muestren todas las variables de entorno en el archivo de registro de compilación durante las compilaciones de proyectos de C++.

 **No**

Las variables de entorno se excluyen del archivo de registro de compilación.

## <a name="build-timing"></a>Tiempo de compilación

 **Sí**

  Activa el registro de compilación. Si se selecciona, se muestra en la ventana de salida el tiempo que se tarda en completar la compilación. Para más información, consulte [Ventana Resultados](../../ide/reference/output-window.md).

 **No**

Desactiva el registro de compilación.

## <a name="maximum-concurrent-c-compilations"></a>Máximo de compilaciones de C++ concurrentes

Especifica el número máximo de núcleos de CPU que se usarán para la compilación paralela de C++.

## <a name="extensions-to-include"></a>Extensiones para incluir

Especifica las extensiones de nombre de archivo de los archivos que se pueden importar al proyecto.

## <a name="extensions-to-hide"></a>Extensiones para ocultar

Especifica las extensiones de nombre de archivo de los archivos que no aparecerán en el **Explorador de soluciones** cuando esté habilitada la opción **Mostrar todos los archivos**.

## <a name="build-customization-search-path"></a>Ruta de búsqueda de personalizaciones de compilación

Especifica la lista de directorios que contienen archivos .rules, que ayudan a definir reglas de compilación para los proyectos.

## <a name="solution-explorer-mode"></a>Modo Explorador de soluciones

**Mostrar únicamente archivos del proyecto**

Configura el **Explorador de soluciones** de modo que solo muestre archivos del proyecto.

**Mostrar todos los archivos**

Configura el **Explorador de soluciones** de modo que muestre tanto archivos del proyecto como archivos del disco en la carpeta del proyecto.

## <a name="enable-project-caching"></a>Habilitar almacenamiento en caché de los proyectos

**Sí**

Permite que Visual Studio almacene en caché los datos del proyecto para que, cuando lo abra la próxima vez, se carguen esos datos en lugar de volver a calcularlos desde los archivos de proyecto. Usar datos en caché puede acelerar de forma significativa el tiempo de carga de un proyecto.

**No**

No se usan los datos de proyecto almacenados en caché. Se analizan los archivos de proyecto cada vez que se cargue el proyecto.

## <a name="see-also"></a>Consulte también

- [Compilación de programas de C/C++](/cpp/build/projects-and-build-systems-cpp)
- [Referencia de compilación de C/C++](/cpp/build/reference/c-cpp-building-reference)
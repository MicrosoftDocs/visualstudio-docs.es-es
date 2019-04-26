---
title: Propiedades de proyectos generales (C++ para Android) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
author: corob
ms.author: mblome
manager: jillfra
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 4bb6f26fe40b639b43cb803577a785fa9b48823d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818952"
---
# <a name="general-project-properties-android-c"></a>Propiedades de proyectos generales (C++ para Android)

Propiedad. | Descripción | Opciones
--- | ---| ---
Directorio de salida | Especifica una ruta de acceso relativa al directorio de archivos de salida; puede incluir variables de entorno.
Directorio intermedio | Especifica una ruta de acceso relativa al directorio de archivos intermedios; puede incluir variables de entorno.
Nombre de destino | Especifica el nombre del archivo que generará el proyecto.
Extensión de destino | Especifica una extensión de archivo que generará este proyecto. (Ejemplo: *.exe* o *.dll*)
Extensiones para eliminar al limpiar | Especificación de comodines delimitados por punto y coma para indicar qué archivos del directorio de archivos intermedios se deben eliminar al limpiar o recompilar.
Archivo de registro de compilación | Especifica el archivo de registro de compilación en el que se escribe cuando está habilitada la opción de registro de compilación.
Conjunto de herramientas de la plataforma | Especifica el conjunto de herramientas usado para compilar la configuración actual. Si no se establece, se usa el conjunto de herramientas predeterminado.
Tipo de configuración | Especifica el tipo de salida que genera esta configuración. | **Biblioteca dinámica (.so)**: biblioteca dinámica (*.so*)<br>**Biblioteca estática (.a)**: biblioteca estática (*.a*)<br>**Utilidad**: utilidad<br>**Archivo Make**: archivo Make<br>
Nivel de API de destino | Nivel de la API del NDK de Android que es el destino de la configuración.
Uso de STL | Especifica la biblioteca estándar de C++ que se usará para esta configuración. | **Biblioteca en tiempo de ejecución de C++ mínima (system)**<br>**Biblioteca estática en tiempo de ejecución de C++ (gabi++_static)**<br>**Biblioteca compartida en tiempo de ejecución de C++ (gabi++_shared)**<br>**Biblioteca estática en tiempo de ejecución de STLport (stlport_static)**<br>**Biblioteca compartida en tiempo de ejecución de STLport (stlport_shared)**<br>**Biblioteca estática de GNU STL (gnustl_static)**<br>**Biblioteca compartida de GNU STL (gnustl_shared)**<br>**Biblioteca estática de LLVM libc++ (c++_static)**<br>**Biblioteca compartida de LLVM libc++ (c++_shared)**<br>
Modo Thumb | Cree código que se ejecuta para la microarquitectura Thumb. Solo es válido para la arquitectura ARM. | **Thumb**<br>**Arm**<br>**Deshabilitado**<br>

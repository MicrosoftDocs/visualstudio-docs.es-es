---
title: Propiedades de proyectos generales (archivos Make de C++ para Android) | Microsoft Docs
ms.custom: 
ms.date: 10/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
author: corob
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
ms.openlocfilehash: d7105b75328175abcaba98d062ebeb591ce72d46
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="general-project-properties-android-c-makefile"></a>Propiedades de proyectos generales (archivos Make de C++ para Android)

Propiedad | Descripción | Opciones
--- | ---| ---
Directorio de salida | Especifica una ruta de acceso relativa al directorio de archivos de salida; puede incluir variables de entorno.
Directorio intermedio | Especifica una ruta de acceso relativa al directorio de archivos intermedios; puede incluir variables de entorno.
Archivo de registro de compilación | Especifica el archivo de registro de compilación en el que se escribe cuando está habilitada la opción de registro de compilación.
Tipo de configuración | Especifica el tipo de salida que genera esta configuración. | **Biblioteca dinámica (.so)**: biblioteca dinámica (.so)<br>**Biblioteca estática (.a)**: biblioteca estática (.a)<br>**Utilidad** : utilidad<br>**Archivo Make**: archivo Make<br>

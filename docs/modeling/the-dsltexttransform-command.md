---
title: El comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a3605dd3d6cd7615a2afd4dba18bf2f7bed994f4
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
DslTextTransform.cmd es una secuencia de comandos que llama a TextTransform.exe y ejecuta con opciones comunes. Puede usar DslTextTransformation.cmd para automatizar una compilación nocturna de su [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proyectos. Para obtener más información, consulte [generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd se encuentra en el siguiente directorio:

 **\<Ruta de instalación de Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Puede especificar los siguientes argumentos como entrada para DslTextTransform.cmd:

-   El directorio de salida del proyecto de modelo de dominio.

-   El directorio de salida del proyecto de definición del diseñador.

-   La ubicación del archivo de plantilla de texto.

 DslTextTransform.cmd procesa el archivo de plantilla de texto especificado mediante los ensamblados y los procesadores de directivas de forma predeterminada. Si creas procesadores de directivas personalizadas, puede crear su propio archivo de lote que llama a TextTransform.exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.
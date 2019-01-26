---
title: El comando DslTextTransform
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 97ddf1fb9dd9e59c2d00f3733069a5cdb14553bf
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037907"
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
DslTextTransform.cmd es un script que llame a TextTransform.exe y lo ejecuta con opciones comunes. Puede usar para automatizar una compilación nocturna de DslTextTransformation.cmd su [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proyectos. Para obtener más información, consulte [generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd se encuentra en el directorio siguiente:

 **\<Ruta de instalación de Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Puede especificar los argumentos siguientes como entrada para DslTextTransform.cmd:

- El directorio de salida del proyecto de modelo de dominio.

- El directorio de salida del proyecto de definición del diseñador.

- La ubicación del archivo de plantilla de texto.

  DslTextTransform.cmd procesa el archivo de plantilla de texto especificado utilizando los ensamblados y los procesadores de directivas predeterminado. Si crea los procesadores de directivas personalizados, puede crear su propio archivo de lote que llama a TextTransform.exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.
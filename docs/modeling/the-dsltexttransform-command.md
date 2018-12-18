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
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 8c1be8b041fcf5f4eb70b37a53b7c32705f6cfcf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49876625"
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
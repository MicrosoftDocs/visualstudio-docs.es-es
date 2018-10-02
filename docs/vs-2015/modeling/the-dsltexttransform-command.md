---
title: El comando DslTextTransform | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8a565fa6226348a1fe1b6dcfcbb67f704e74abc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578209"
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [el comando DslTextTransform](https://docs.microsoft.com/visualstudio/modeling/the-dsltexttransform-command).  
  
DslTextTransform.cmd es un script que llame a TextTransform.exe y lo ejecuta con opciones comunes. Puede usar para automatizar una compilación nocturna de DslTextTransformation.cmd su [!INCLUDE[dsl](../includes/dsl-md.md)] proyectos. Para obtener más información, consulte [generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd se encuentra en el directorio siguiente:  
  
 **\<Ruta de instalación de Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**  
  
 Puede especificar los argumentos siguientes como entrada para DslTextTransform.cmd:  
  
-   El directorio de salida del proyecto de modelo de dominio.  
  
-   El directorio de salida del proyecto de definición del diseñador.  
  
-   La ubicación del archivo de plantilla de texto.  
  
 DslTextTransform.cmd procesa el archivo de plantilla de texto especificado utilizando los ensamblados y los procesadores de directivas predeterminado. Si crea los procesadores de directivas personalizados, puede crear su propio archivo de lote que llama a TextTransform.exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.




---
title: El comando DslTextTransform | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: 882d2c8d0dec5e4673b24436067bd6255c2052be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853160"
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform.cmd es un script que llame a TextTransform.exe y lo ejecuta con opciones comunes. Puede usar para automatizar una compilación nocturna de DslTextTransformation.cmd su [!INCLUDE[dsl](../includes/dsl-md.md)] proyectos. Para obtener más información, consulte [generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).  
  
 DslTextTransform.cmd se encuentra en el directorio siguiente:  
  
 **\<Ruta de instalación de Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**  
  
 Puede especificar los argumentos siguientes como entrada para DslTextTransform.cmd:  
  
- El directorio de salida del proyecto de modelo de dominio.  
  
- El directorio de salida del proyecto de definición del diseñador.  
  
- La ubicación del archivo de plantilla de texto.  
  
  DslTextTransform.cmd procesa el archivo de plantilla de texto especificado utilizando los ensamblados y los procesadores de directivas predeterminado. Si crea los procesadores de directivas personalizados, puede crear su propio archivo de lote que llama a TextTransform.exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.




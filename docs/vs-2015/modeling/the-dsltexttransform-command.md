---
title: El comando DslTextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
ms.assetid: 7d025d0b-6543-4a49-9f6b-8b8cfcad77ee
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 599bf14a3d37fbd6bdff111f79e658f44624792b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658461"
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DslTextTransform. cmd es un script que llama a TextTransform. exe y lo ejecuta con opciones comunes. Puede usar DslTextTransformation. cmd para automatizar una compilación nocturna de los proyectos de [!INCLUDE[dsl](../includes/dsl-md.md)]. Para obtener más información, vea [generar archivos con la utilidad textTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd se encuentra en el siguiente directorio:

 **Ruta de instalación de \<Visual Studio SDK > \VisualStudioIntegration\Tools\Bin**

 Puede especificar los siguientes argumentos como entrada para DslTextTransform. cmd:

- El directorio de salida del proyecto de modelo de dominio.

- El directorio de salida del proyecto de definición del diseñador.

- Ubicación del archivo de plantilla de texto.

  DslTextTransform. cmd procesa el archivo de plantilla de texto especificado con los procesadores y ensamblados de directivas predeterminados. Si crea procesadores de directivas personalizados, puede crear su propio archivo por lotes que llama a TextTransform. exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.

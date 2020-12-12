---
title: El comando DslTextTransform
description: Obtenga información sobre que DslTextTransform. cmd es un script que llama a TextTransform.exe y lo ejecuta con opciones comunes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74f87f735f5ad6864082046327bc852d5d43fdb6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362722"
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
DslTextTransform. cmd es un script que llama a TextTransform.exe y lo ejecuta con opciones comunes. Puede usar DslTextTransformation. cmd para automatizar una compilación nocturna de sus [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proyectos. Para obtener más información, vea [generar archivos con la utilidad textTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform. cmd se encuentra en el siguiente directorio:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Puede especificar los siguientes argumentos como entrada para DslTextTransform. cmd:

- El directorio de salida del proyecto de modelo de dominio.

- El directorio de salida del proyecto de definición del diseñador.

- Ubicación del archivo de plantilla de texto.

  DslTextTransform. cmd procesa el archivo de plantilla de texto especificado con los procesadores y ensamblados de directivas predeterminados. Si crea procesadores de directivas personalizados, puede crear su propio archivo por lotes que llama a TextTransform.exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.

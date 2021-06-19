---
title: El comando DslTextTransform
description: Aprenda que DslTextTransform.cmd es un script que llama a TextTransform.exe y lo ejecuta con opciones comunes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, commands
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65d1e1d02c5b7d13c2e86343c6307306542d00e2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388651"
---
# <a name="the-dsltexttransform-command"></a>El comando DslTextTransform
DslTextTransform.cmd es un script que llama a TextTransform.exe y lo ejecuta con opciones comunes. Puede usar DslTextTransformation.cmd para automatizar una compilación nocturna de los [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] proyectos. Para obtener más información, vea [Generar archivos con la utilidad TextTransform](../modeling/generating-files-with-the-texttransform-utility.md).

 DslTextTransform.cmd se encuentra en el directorio siguiente:

 **\<Visual Studio SDK Installation Path>\VisualStudioIntegration\Tools\Bin**

 Puede especificar los argumentos siguientes como entrada para DslTextTransform.cmd:

- Directorio de salida del proyecto de modelo de dominio.

- Directorio de salida del proyecto de definición del diseñador.

- Ubicación del archivo de plantilla de texto.

  DslTextTransform.cmd procesa el archivo de plantilla de texto especificado mediante los procesadores de directivas y ensamblados predeterminados. Si crea procesadores de directivas personalizadas, puede crear su propio archivo por lotes que llame a TextTransform.exe. En este archivo por lotes, puede especificar los ensamblados y los procesadores de directivas personalizados asociados.

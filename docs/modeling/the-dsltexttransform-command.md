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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f51d1a5cbefc3c2cf60559075a9c9a299664ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924499"
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

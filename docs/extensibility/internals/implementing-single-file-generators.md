---
title: Implementación de Single-File generadores de | Microsoft Docs
description: Obtenga información sobre cómo usar una herramienta personalizada que implementa la interfaz IVsSingleFileGenerator para ampliar los sistemas de proyectos de Visual Basic y Visual C# en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 11ce8a69841d18d383e9d8e12c14d7af652d9cb8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900049"
---
# <a name="implementing-single-file-generators"></a>Implementación de generadores de un solo archivo
Una herramienta personalizada , a veces denominada generador de archivos único, se puede usar para extender los [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] sistemas de proyecto y en [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Una herramienta personalizada es un componente COM que implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz . Con esta interfaz, una herramienta personalizada transforma un único archivo de entrada en un único archivo de salida. El resultado de la transformación puede ser código fuente o cualquier otra salida útil. Dos ejemplos de archivos de código personalizados generados por herramientas son el código generado en respuesta a los cambios en un diseñador visual y los archivos generados mediante el Lenguaje de descripción de servicios Web (WSDL).

 Cuando se carga una herramienta personalizada o se guarda el archivo de entrada, el sistema del proyecto llama al método y pasa una referencia a una interfaz de devolución de llamada, por la que la herramienta puede notificar su progreso al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> usuario.

 El archivo de salida que genera la herramienta personalizada se agrega al proyecto con una dependencia en el archivo de entrada. El sistema del proyecto determina automáticamente el nombre del archivo de salida, en función de la cadena devuelta por la implementación de la herramienta personalizada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .

 Una herramienta personalizada debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz . Opcionalmente, las herramientas personalizadas admiten <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> la interfaz para recuperar información de orígenes distintos del archivo de entrada. En cualquier caso, para poder usar una herramienta personalizada, debe registrarla en el sistema o en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro local. Para obtener más información sobre el registro de herramientas [personalizadas, vea Registrar generadores de archivos únicos.](../../extensibility/internals/registering-single-file-generators.md)

## <a name="see-also"></a>Consulta también
- [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)

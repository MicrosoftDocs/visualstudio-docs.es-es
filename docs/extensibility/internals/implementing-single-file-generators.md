---
title: Implementar generadores de un único archivo | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a7207bf7d846381ea0cbf678ca7afe3d3d177b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335102"
---
# <a name="implementing-single-file-generators"></a>Implementación de generadores de un solo archivo
Una herramienta personalizada: a veces se denomina un generador de archivos únicos, se puede usar para extender el [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] en los sistemas del proyecto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Una herramienta personalizada es un componente COM que implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz. Uso de esta interfaz, una herramienta personalizada transforma un archivo de entrada en un único archivo de salida. El resultado de la transformación puede ser código fuente, o cualquier otro de salida que resulta útil. Dos ejemplos de archivos de código generados por la herramienta personalizada son código generado en respuesta a cambios en un diseñador visual y los archivos generados mediante el lenguaje de descripción de servicios Web (WSDL).

 Cuando se carga una herramienta personalizada o se guarda el archivo de entrada, el sistema del proyecto se llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método y pasa una referencia a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfaz de devolución de llamada, mediante el cual la herramienta puede notificar el progreso al usuario.

 El archivo de salida que genera la herramienta personalizada se agrega al proyecto con una dependencia en el archivo de entrada. El sistema del proyecto determina automáticamente el nombre del archivo de salida, en función de la cadena devuelta por la implementación de la herramienta personalizada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.

 Una herramienta personalizada debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz. Si lo desea, las herramientas personalizadas admiten el <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfaz para recuperar información de orígenes que no sea el archivo de entrada. En cualquier caso, para poder usar una herramienta personalizada, debe registrarlo con el sistema o en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro local. Para obtener más información sobre cómo registrar herramientas personalizadas, vea [registrar generadores de único archivo](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Vea también
- [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)
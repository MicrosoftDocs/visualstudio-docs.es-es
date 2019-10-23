---
title: Implementación de generadores de un solo archivo | Microsoft Docs
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
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727178"
---
# <a name="implementing-single-file-generators"></a>Implementación de generadores de un solo archivo
Una herramienta personalizada, a la que a veces se hace referencia como generador de un solo archivo, se puede usar para ampliar los sistemas de proyectos de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Una herramienta personalizada es un componente COM que implementa la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Mediante esta interfaz, una herramienta personalizada transforma un único archivo de entrada en un único archivo de salida. El resultado de la transformación puede ser código fuente o cualquier otro resultado que sea útil. Dos ejemplos de archivos de código generados por la herramienta personalizados son el código generado en respuesta a los cambios en un diseñador visual y los archivos generados con el lenguaje de descripción de servicios web (WSDL).

 Cuando se carga una herramienta personalizada o se guarda el archivo de entrada, el sistema del proyecto llama al método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> y pasa una referencia a una interfaz de devolución de llamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>, en la que la herramienta puede informar sobre su progreso al usuario.

 El archivo de salida que genera la herramienta personalizada se agrega al proyecto con una dependencia en el archivo de entrada. El sistema del proyecto determina automáticamente el nombre del archivo de salida, en función de la cadena devuelta por la implementación de la herramienta personalizada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.

 Una herramienta personalizada debe implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Opcionalmente, las herramientas personalizadas admiten la interfaz de <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> para recuperar información de orígenes distintos del archivo de entrada. En cualquier caso, antes de poder usar una herramienta personalizada, debe registrarla en el sistema o en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro local. Para obtener más información sobre el registro de herramientas personalizadas, vea [registrar generadores de archivos únicos](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Vea también
- [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)
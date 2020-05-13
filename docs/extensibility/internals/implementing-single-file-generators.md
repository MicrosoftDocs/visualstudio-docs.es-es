---
title: Implementación de generadores de un solo archivo Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707655"
---
# <a name="implementing-single-file-generators"></a>Implementación de generadores de un solo archivo
Una herramienta personalizada, a veces denominada un único generador [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] de archivos, se puede utilizar para ampliar los sistemas y proyectos en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Una herramienta personalizada es un componente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM que implementa la interfaz. Con esta interfaz, una herramienta personalizada transforma un único archivo de entrada en un único archivo de salida. El resultado de la transformación puede ser código fuente o cualquier otra salida que sea útil. Dos ejemplos de archivos de código generados por herramientas personalizadas son código generado en respuesta a los cambios en un diseñador visual y los archivos generados mediante el lenguaje de descripción de servicios web (WSDL).

 Cuando se carga una herramienta personalizada o se guarda el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> archivo de entrada, el <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> sistema del proyecto llama al método y pasa una referencia a una interfaz de devolución de llamada, por lo que la herramienta puede notificar su progreso al usuario.

 El archivo de salida que genera la herramienta personalizada se agrega al proyecto con una dependencia en el archivo de entrada. El sistema de proyectos determina automáticamente el nombre del archivo de salida, en <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>función de la cadena devuelta por la implementación de la herramienta personalizada de .

 Una herramienta personalizada <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> debe implementar la interfaz. Opcionalmente, las herramientas <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> personalizadas admiten la interfaz para recuperar información de orígenes distintos del archivo de entrada. En cualquier caso, antes de poder utilizar una herramienta personalizada, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debe registrarla en el sistema o en el registro local. Para obtener más información sobre el registro de herramientas personalizadas, consulte Registro de generadores de [archivos únicos](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Vea también
- [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)

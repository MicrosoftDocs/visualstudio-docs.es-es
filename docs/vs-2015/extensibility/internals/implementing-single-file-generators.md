---
title: Implementar generadores de un único archivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f77b8dd1f28431665aae5d6c64da58d038a156b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49300973"
---
# <a name="implementing-single-file-generators"></a>Implementación de generadores de un solo archivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una herramienta personalizada: a veces se denomina un generador de archivos únicos, se puede usar para extender el [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] y [!INCLUDE[csprcs](../../includes/csprcs-md.md)] en los sistemas del proyecto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Una herramienta personalizada es un componente COM que implementa el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz. Uso de esta interfaz, una herramienta personalizada transforma un archivo de entrada en un único archivo de salida. El resultado de la transformación puede ser código fuente, o cualquier otro de salida que resulta útil. Dos ejemplos de archivos de código generados por la herramienta personalizada son código generado en respuesta a cambios en un diseñador visual y los archivos generados mediante el lenguaje de descripción de servicios Web (WSDL).  
  
 Cuando se carga una herramienta personalizada o se guarda el archivo de entrada, el sistema del proyecto se llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método y pasa una referencia a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfaz de devolución de llamada, mediante el cual la herramienta puede notificar el progreso al usuario.  
  
 El archivo de salida que genera la herramienta personalizada se agrega al proyecto con una dependencia en el archivo de entrada. El sistema del proyecto determina automáticamente el nombre del archivo de salida, en función de la cadena devuelta por la implementación de la herramienta personalizada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Una herramienta personalizada debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz. Si lo desea, las herramientas personalizadas admiten el <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfaz para recuperar información de orígenes que no sea el archivo de entrada. En cualquier caso, para poder usar una herramienta personalizada, debe registrarlo con el sistema o en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registro local. Para obtener más información sobre cómo registrar herramientas personalizadas, vea [registrar generadores de único archivo](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Vea también  
 [Determinar el Namespace predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)


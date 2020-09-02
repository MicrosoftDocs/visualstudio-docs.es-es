---
title: Implementación de generadores de un solo archivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192693"
---
# <a name="implementing-single-file-generators"></a>Implementación de generadores de un solo archivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una herramienta personalizada, que a veces se denomina generador de un solo archivo, se puede usar para extender los [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] sistemas de proyectos de y en [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Una herramienta personalizada es un componente COM que implementa la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz. Mediante esta interfaz, una herramienta personalizada transforma un único archivo de entrada en un único archivo de salida. El resultado de la transformación puede ser código fuente o cualquier otro resultado que sea útil. Dos ejemplos de archivos de código generados por la herramienta personalizados son el código generado en respuesta a los cambios en un diseñador visual y los archivos generados con el lenguaje de descripción de servicios web (WSDL).  
  
 Cuando se carga una herramienta personalizada o se guarda el archivo de entrada, el sistema del proyecto llama al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método y pasa una referencia a una <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfaz de devolución de llamada, por lo que la herramienta puede informar sobre su progreso al usuario.  
  
 El archivo de salida que genera la herramienta personalizada se agrega al proyecto con una dependencia en el archivo de entrada. El sistema del proyecto determina automáticamente el nombre del archivo de salida, en función de la cadena devuelta por la implementación de la herramienta personalizada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Una herramienta personalizada debe implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaz. Opcionalmente, las herramientas personalizadas admiten la <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfaz para recuperar información de orígenes distintos del archivo de entrada. En cualquier caso, antes de poder usar una herramienta personalizada, debe registrarla en el sistema o en el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] registro local. Para obtener más información sobre el registro de herramientas personalizadas, vea [registrar generadores de archivos únicos](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Consulte también  
 [Determinar el espacio de nombres predeterminado de un proyecto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Exposición de tipos a diseñadores visuales](../../extensibility/internals/exposing-types-to-visual-designers.md)

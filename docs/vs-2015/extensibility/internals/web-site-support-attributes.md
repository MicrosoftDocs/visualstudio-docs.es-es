---
title: Atributos de compatibilidad del sitio web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144308"
---
# <a name="web-site-support-attributes"></a>Atributos de compatibilidad del sitio web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] El proyecto de sitio web se puede extender para proporcionar compatibilidad con los lenguajes de programación web. El idioma debe registrarse con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para que las plantillas de proyecto puedan aparecer en el cuadro de diálogo **nuevo sitio web** cuando se seleccione el idioma.  
  
 El ejemplo de IronPython Studio incluye compatibilidad con sitios Web. Puede encontrarlo con los [ejemplos de VSSDK](../../misc/vssdk-samples.md). Incluye las siguientes clases de atributos para registrar IronPython como lenguaje Codebehind para proyectos web nuevos.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Este atributo se coloca en el proyecto de lenguaje. Agrega el idioma a la lista de lenguajes de programación web en **la lista de idiomas del** cuadro de diálogo **nuevo sitio web** . Por ejemplo, lo siguiente agrega IronPython a la lista:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Este atributo también establece la ruta de acceso de las plantillas para que apunte a la carpeta de plantillas. Para obtener más información acerca de la ubicación de la carpeta de plantillas, consulte [plantillas de soporte del sitio web](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Este atributo se coloca en el proyecto de lenguaje. Permite que el proyecto de sitio web Anide un tipo de archivo (relacionado) bajo otro tipo de archivo (principal) en el **Explorador de soluciones**.  
  
 Por ejemplo:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Especifica que un archivo de código subyacente de IronPython está relacionado con un archivo. aspx. Cuando se crea una nueva página web. aspx en una solución de sitio web de IronPython, se genera un nuevo archivo de origen. py y aparece como un nodo secundario de la página. aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Este atributo se coloca en el paquete de proyecto de lenguaje. Selecciona el proveedor de IntelliSense para el lenguaje.  
  
 Por ejemplo:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Especifica que se debe crear una instancia de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , a petición para proporcionar servicios de lenguaje.  
  
 La implementación de IVsIntellisenseProject controla las referencias y llama al compilador de lenguaje cuando se solicita una página web con código, pero no se almacena en caché.  
  
## <a name="see-also"></a>Consulte también  
 [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)

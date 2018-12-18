---
title: Atributos de compatibilidad del sitio Web | Documentos de Microsoft
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
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 312d8a760cc7005afc4308b637b12a292bd20329
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756679"
---
# <a name="web-site-support-attributes"></a>Atributos de compatibilidad del sitio web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Proyecto de sitio Web puede ampliarse para proporcionar compatibilidad con Web lenguajes de programación. El lenguaje debe registrarse con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para que las plantillas de proyecto pueden aparecer en el **nuevo sitio Web** cuadro de diálogo cuando se selecciona el idioma.  
  
 El ejemplo de IronPython Studio incluye compatibilidad con sitios web. Puede encontrarlo con el [muestras de VSSDK](../../misc/vssdk-samples.md). Incluye las siguientes clases de atributo para registrar IronPython como un lenguaje de código subyacente para los nuevos proyectos Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Este atributo se coloca en el proyecto de lenguaje. Agrega el idioma a la lista de lenguajes de programación en el Web la **lenguaje** lista en el **nuevo sitio Web** cuadro de diálogo. Por ejemplo, el siguiente agrega IronPython a la lista:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Este atributo también establece la ruta de acceso de las plantillas para que apunte a la carpeta de plantillas. Para obtener más información sobre la ubicación de la carpeta de plantillas, consulte [plantillas de sitio Web de soporte técnico](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Este atributo se coloca en el proyecto de lenguaje. Permite que el proyecto de sitio Web anidar un tipo de archivo (relacionado) bajo otro tipo de archivo (principal) en el **el Explorador de soluciones**.  
  
 Por ejemplo:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Especifica que un archivo de código subyacente de IronPython está relacionado con un archivo .aspx. Cuando se crea una nueva página Web de aspx en una solución de sitio IronPython Web, un nuevo archivo de origen py se genera y aparece como un nodo secundario de la página aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Este atributo se coloca en el paquete de idioma del proyecto. Selecciona el proveedor de Intellisense para el lenguaje.  
  
 Por ejemplo:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Especifica que una instancia de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, debe crearse a petición para proporcionar servicios de lenguaje.  
  
 La implementación de IVsIntellisenseProject controla las referencias y llama al compilador del lenguaje cuando se solicita una página Web con código, pero no se almacena en caché.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con sitios web](../../extensibility/internals/web-site-support.md)


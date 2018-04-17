---
title: Atributos de soporte técnico del sitio Web | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="web-site-support-attributes"></a>Atributos de soporte técnico del sitio Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proyecto de sitio Web puede ampliarse para proporcionar compatibilidad para Web lenguajes de programación. El lenguaje debe registrarse con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que las plantillas de proyecto pueden aparecer en el **nuevo sitio Web** cuadro de diálogo cuando se selecciona el idioma.

El ejemplo de IronPython Studio incluye compatibilidad con sitios web. El ejemplo contiene las siguientes clases de atributo para registrar IronPython como un lenguaje de código subyacente para los nuevos proyectos Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Este atributo se coloca en el proyecto de lenguaje. El idioma agrega a la lista de lenguajes de programación en el Web la **lenguaje** lista en la **nuevo sitio Web** cuadro de diálogo. Por ejemplo, el código siguiente agrega IronPython a la lista:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Este atributo también establece la ruta de acceso de plantillas para que apunte a la carpeta de plantillas. Para obtener más información sobre la ubicación de la carpeta de plantillas, consulte [plantillas de sitio Web de soporte técnico](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Este atributo se coloca en el proyecto de lenguaje. Permite al proyecto de sitio Web anidar un tipo de archivo (relacionado) en otro tipo de archivo (principal) en el **el Explorador de soluciones**.

 Por ejemplo, el código siguiente especifica que un archivo de código subyacente de IronPython está relacionado con un archivo .aspx. Cuando se crea una nueva página Web de aspx en una solución de sitio IronPython Web, un nuevo archivo de origen .py se genera y aparece como un nodo secundario de la página aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Este atributo se coloca en el paquete de idioma del proyecto. Selecciona el proveedor de IntelliSense para el lenguaje.

 Por ejemplo, el código siguiente especifica que una instancia de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, deben crearse a petición para proporcionar servicios de lenguaje.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 La implementación de IVsIntellisenseProject controla las referencias y llama al compilador del lenguaje cuando se solicita una página Web con código, pero no está almacenado en memoria caché.

## <a name="see-also"></a>Vea también
 [Compatibilidad con sitios web](../../extensibility/internals/web-site-support.md)
---
title: Atributos de compatibilidad del sitio web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703494"
---
# <a name="web-site-support-attributes"></a>Atributos de compatibilidad del sitio web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] El proyecto de sitio web se puede extender para proporcionar compatibilidad con los lenguajes de programación web. El idioma debe registrarse con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para que las plantillas de proyecto puedan aparecer en el cuadro de diálogo **nuevo sitio web** cuando se seleccione el idioma.

El ejemplo de IronPython Studio incluye compatibilidad con sitios Web. El ejemplo contiene las siguientes clases de atributos para registrar IronPython como lenguaje Codebehind para proyectos web nuevos.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Este atributo se coloca en el proyecto de lenguaje. Agrega el idioma a la lista de lenguajes de programación web en **la lista de idiomas del** cuadro de diálogo **nuevo sitio web** . Por ejemplo, el código siguiente agrega IronPython a la lista:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Este atributo también establece la ruta de acceso de las plantillas para que apunte a la carpeta de plantillas. Para obtener más información acerca de la ubicación de la carpeta de plantillas, consulte [plantillas de soporte del sitio web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Este atributo se coloca en el proyecto de lenguaje. Permite que el proyecto de sitio web Anide un tipo de archivo (relacionado) bajo otro tipo de archivo (principal) en el **Explorador de soluciones**.

 Por ejemplo, el código siguiente especifica que un archivo de código subyacente de IronPython está relacionado con un archivo. aspx. Cuando se crea una nueva página web. aspx en una solución de sitio web de IronPython, se genera un nuevo archivo de origen. py y aparece como un nodo secundario de la página. aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Este atributo se coloca en el paquete de proyecto de lenguaje. Selecciona el proveedor de IntelliSense para el lenguaje.

 Por ejemplo, el código siguiente especifica que una instancia de PythonIntellisenseProvider, que implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , debe crearse a petición para proporcionar servicios de lenguaje.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 La implementación de IVsIntellisenseProject controla las referencias y llama al compilador de lenguaje cuando se solicita una página web con código pero no se almacena en caché.

## <a name="see-also"></a>Vea también
- [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)

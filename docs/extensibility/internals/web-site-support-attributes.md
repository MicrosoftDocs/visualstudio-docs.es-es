---
title: Atributos de soporte de sitios web ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703494"
---
# <a name="web-site-support-attributes"></a>Atributos de compatibilidad del sitio web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]El proyecto de sitio web se puede ampliar para proporcionar compatibilidad con lenguajes de programación web. El idioma debe [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrarse para que las plantillas de proyecto puedan aparecer en el cuadro de diálogo **Nuevo sitio Web** cuando se seleccione el idioma.

El ejemplo de IronPython Studio incluye compatibilidad con sitios web. El ejemplo contiene las siguientes clases de atributo para registrar IronPython como un lenguaje de código subyacente para nuevos proyectos Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Este atributo se coloca en el proyecto de lenguaje. Agrega el idioma a la lista de lenguajes de programación Web en la lista **Idioma** del cuadro de diálogo **Nuevo sitio Web.** Por ejemplo, el código siguiente agrega IronPython a la lista:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Este atributo también establece la ruta de acceso de las plantillas para que apunte a la carpeta templates. Para obtener más información sobre la ubicación de la carpeta de plantillas, vea Plantillas de [compatibilidad con sitios web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Este atributo se coloca en el proyecto de lenguaje. Permite que el proyecto de sitio Web anide un tipo de archivo (relacionado) en otro tipo de archivo (primario) en el Explorador de **soluciones**.

 Por ejemplo, el código siguiente especifica que un archivo de código subyacente IronPython está relacionado con un archivo .aspx. Cuando se crea una nueva página Web .aspx en una solución de sitio Web de IronPython, se genera un nuevo archivo de origen .py y aparece como un nodo secundario de la página .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Este atributo se coloca en el paquete de proyecto de idioma. Selecciona el proveedor IntelliSense para el idioma.

 Por ejemplo, el código siguiente especifica que se debe crear <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>una instancia de PythonIntellisenseProvider, que implementa , a petición para proporcionar servicios de lenguaje.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 El IVsIntellisenseProject implementación controla las referencias y llama al compilador de lenguaje cuando se solicita una página Web con código, pero no se almacena en caché.

## <a name="see-also"></a>Vea también
- [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)

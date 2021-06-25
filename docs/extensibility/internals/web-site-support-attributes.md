---
title: Atributos de compatibilidad del sitio web | Microsoft Docs
description: Obtenga información sobre los atributos de compatibilidad del sitio web necesarios para ampliar la funcionalidad de Visual Studio mediante proyectos de sitio web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 348fd16234e38cd7832ae18e7b28e6abe0bc63d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901778"
---
# <a name="web-site-support-attributes"></a>Atributos de compatibilidad del sitio web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] El proyecto de sitio web se puede ampliar para proporcionar compatibilidad con lenguajes de programación web. El idioma debe registrarse con para que las plantillas de proyecto puedan aparecer en el cuadro de diálogo Nuevo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **sitio web** cuando se selecciona el idioma.

El ejemplo de IronPython Studio incluye compatibilidad con sitios web. El ejemplo contiene las siguientes clases de atributo para registrar IronPython como un lenguaje de código posterior para nuevos proyectos web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Este atributo se coloca en el proyecto de lenguaje. Agrega el lenguaje a la lista de lenguajes de programación web de la **lista Lenguaje** del cuadro **de diálogo** Nuevo sitio web . Por ejemplo, el código siguiente agrega IronPython a la lista:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Este atributo también establece la ruta de acceso de las plantillas para que apunte a la carpeta templates. Para obtener más información sobre la ubicación de la carpeta templates, vea [Plantillas de soporte técnico de sitios web.](../../extensibility/internals/web-site-support-templates.md)

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Este atributo se coloca en el proyecto de lenguaje. Permite al proyecto de sitio web anidar un tipo de archivo (relacionado) en otro tipo de archivo (principal) en el **Explorador de soluciones**.

 Por ejemplo, el código siguiente especifica que un archivo codebehind de IronPython está relacionado con un archivo .aspx. Cuando se crea una nueva página web .aspx en una solución de sitio web de IronPython, se genera un nuevo archivo de código fuente .py y aparece como nodo secundario de la página .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Este atributo se coloca en el paquete de proyecto de lenguaje. Selecciona el proveedor de IntelliSense para el idioma.

 Por ejemplo, el código siguiente especifica que se debe crear una instancia de PythonIntellisenseProvider, que implementa , a <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> petición para proporcionar servicios de lenguaje.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 La implementación de IVsIntellisenseProject controla las referencias y llama al compilador de lenguaje cuando se solicita una página web con código, pero no se almacena en caché.

## <a name="see-also"></a>Consulta también
- [Compatibilidad del sitio web](../../extensibility/internals/web-site-support.md)

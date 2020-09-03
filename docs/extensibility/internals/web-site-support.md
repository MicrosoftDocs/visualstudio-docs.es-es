---
title: Compatibilidad con sitios web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703442"
---
# <a name="web-site-support"></a>Compatibilidad del sitio web
Un sistema de proyectos de sitio web es un sistema de proyectos que crea proyectos Web. Los proyectos web a su vez crean aplicaciones Web. Un proyecto de sitio web genera un archivo ejecutable para cada página web que tiene código asociado. Los archivos ejecutables adicionales se generan a partir de los archivos de código fuente en la carpeta/App_Code.

 Los sistemas de proyecto de sitio web se crean mediante la adición de plantillas y atributos de registro a un sistema de proyecto existente. Uno de estos atributos selecciona el proveedor de IntelliSense para el lenguaje. La implementación del proveedor de IntelliSense controla las referencias y llama al compilador de lenguaje cuando se solicita una página web inteligente que no está almacenada en caché.

 El compilador de lenguaje utilizado para compilar páginas web se debe registrar con [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . Puede usar el [ \<compiler> elemento](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) en un archivo de Web.config para registrar el compilador, como en el ejemplo siguiente:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>En esta sección
- [Plantillas de compatibilidad del sitio web](../../extensibility/internals/web-site-support-templates.md)

 Muestra las plantillas que puede usar para crear nuevos proyectos de sitios web y elementos asociados.

- [Atributos de compatibilidad del sitio web](../../extensibility/internals/web-site-support-attributes.md)

 Presenta los atributos de registro que conectan un proyecto de sitio web a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>Secciones relacionadas
- [Proyectos Web](../../extensibility/internals/web-projects.md)

 Presenta información general de los dos tipos de proyectos Web, proyectos de sitio web y proyectos de aplicación Web.

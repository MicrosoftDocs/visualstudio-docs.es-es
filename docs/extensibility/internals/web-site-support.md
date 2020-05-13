---
title: Soporte de sitios web ? Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703442"
---
# <a name="web-site-support"></a>Compatibilidad del sitio web
Un sistema de proyectos de sitio Web es un sistema de proyectos que crea proyectos web. Los proyectos web a su vez crean aplicaciones web. Un proyecto de sitio Web genera un archivo ejecutable para cada página Web que tiene código asociado. Los archivos ejecutables adicionales se generan a partir de los archivos de código fuente de la carpeta /App_Code.

 Los sistemas de proyectos de sitio web se crean agregando plantillas y atributos de registro a un sistema de proyectos existente. Uno de estos atributos selecciona el proveedor intelliSense para el idioma. La implementación del proveedor IntelliSense controla las referencias y llama al compilador de lenguaje cuando se solicita una página Web inteligente que no está almacenada en caché.

 El compilador de lenguaje utilizado para [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]compilar páginas Web debe estar registrado con . Puede utilizar [ \<](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) el compilador> Element en un archivo Web.config para registrar el compilador, como en el ejemplo siguiente:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>En esta sección
- [Plantillas de compatibilidad del sitio web](../../extensibility/internals/web-site-support-templates.md)

 Enumera las plantillas que puede usar para crear nuevos proyectos de sitio Web y elementos asociados.

- [Atributos de compatibilidad del sitio web](../../extensibility/internals/web-site-support-attributes.md)

 Presenta los atributos de registro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]conectan un proyecto de sitio Web a y .

## <a name="related-sections"></a>Secciones relacionadas
- [Proyectos web](../../extensibility/internals/web-projects.md)

 Presenta una visión general de los dos tipos de proyectos web, proyectos de sitio web y proyectos de aplicación web.

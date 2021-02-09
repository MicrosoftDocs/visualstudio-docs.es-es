---
title: Elementos esenciales del proyecto web | Microsoft Docs
description: Obtenga información sobre cómo funcionan los proyectos web en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b071631018ef398be481ccf514b33296e55fc2e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886878"
---
# <a name="web-project-essentials"></a>Conceptos básicos del proyecto web
Los proyectos web crean aplicaciones Web. Puede usar un proyecto web para crear una aplicación web que tiene páginas web inteligentes. Una página web inteligente tiene código del lado servidor que representa la página web a petición.

 Mediante el uso de lenguajes de programación tradicionales, como [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] , puede crear páginas web inteligentes para recopilar y procesar información de un usuario, almacenarla en una base de datos, etc.

- El modelo de código subyacente asocia los archivos de código fuente dependientes con páginas web que tienen la extensión de archivo. aspx o. asmx. Por ejemplo, Hello. aspx podría tener el archivo de código fuente dependiente hello.aspx.cs.

- El código del lado servidor asociado a una página web inteligente se compila en un archivo ejecutable que se encuentra en la carpeta del sitio web/bin.

- Los archivos de código fuente adicionales, como las clases auxiliares que no están asociadas a una página web específica, se encuentran en la carpeta sitio web/App_Code.

  - Un proyecto de sitio web (WSP) genera un archivo ejecutable para cada página web inteligente. Los archivos ejecutables adicionales se generan a partir de los archivos de código fuente de la carpeta/App_Code.

  - Un proyecto de aplicación web (WAP) genera un único archivo ejecutable que combina el código para todas las páginas web inteligentes, así como todos los archivos de origen de la carpeta/App_Code.

- El archivo de solución de un proyecto web se encuentra separado del propio sitio Web. De forma predeterminada, los archivos de solución se encuentran en \Documents and Settings \\ *sucuenta*\Mis Documents \\ *\<Visual Studio ####>* \projects \\ *YourWebSite*.

  > [!NOTE]
  > Si desea conservar el archivo de solución en el sitio web, simplemente muévalo y vuelva a abrirlo.

- Si abre un sitio web que no tiene ningún archivo de solución en Visual Studio, se genera automáticamente un nuevo archivo de solución.

- Los proyectos web no tienen ningún archivo de proyecto. La información del proyecto se almacena en el archivo de la solución, en el archivo web.config y en otro lugar.

- Al agregar propiedades globales a un proyecto Web, se crea automáticamente un archivo de almacenamiento en la carpeta de la solución de proyecto Web.

- Una página web inteligente se puede asociar con un lenguaje de programación del lado servidor mediante la Directiva de página o la \<script runat="server"> etiqueta.

- Además, las páginas web pueden tener cualquier número de bloques de scripting del lado cliente escritos en cualquier lenguaje de scripting.

- Un sistema de proyectos de sitio web se implementa agregando plantillas de proyecto y de elemento y registro al [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] proyecto.

- Un sistema WAP se implementa como un subtipo de proyecto, también denominado tipo de proyecto. El [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] proyecto está calificado por el subtipo WAP para crear el sistema WAP. Para obtener más información sobre los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

- Una página web inteligente combina HTML con un lenguaje de programación del lado servidor. El lenguaje del lado servidor se denomina lenguaje contenido. Para admitir un lenguaje contenido, el sistema del proyecto web debe implementar la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> familia de interfaces.

  - Para admitir el lenguaje contenido en un editor, el servicio del lenguaje HTML debe aplazar la visualización del código de idioma contenido en un servicio de lenguaje contenido.

  - Los marcadores de error (detectores rojos) siempre deben crearse en el búfer primario del editor de código.

## <a name="see-also"></a>Vea también
- [Proyectos web](../../extensibility/internals/web-projects.md)

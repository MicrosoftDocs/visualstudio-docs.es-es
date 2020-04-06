---
title: Fundamentos del proyecto web ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703553"
---
# <a name="web-project-essentials"></a>Conceptos básicos del proyecto web
Los proyectos web crean aplicaciones web. Puede usar un proyecto Web para crear una aplicación web que tenga páginas web inteligentes. Una página Web inteligente tiene código del lado servidor que representa la página Web a petición.

 Mediante el uso de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]lenguajes de programación tradicionales, como o , puede crear páginas Web inteligentes para recopilar y procesar información de un usuario, almacenarla en una base de datos, etc.

- El modelo de código subyacente asocia archivos de código fuente dependientes con páginas Web que tienen la extensión de archivo .aspx o .asmx. Por ejemplo, hello.aspx podría tener el archivo de código fuente dependiente hello.aspx.cs.

- El código del lado servidor asociado a una página Web inteligente se compila en un archivo ejecutable que se encuentra en la carpeta /bin del sitio Web.

- Los archivos de código fuente adicionales, como las clases auxiliares que no están asociadas a una página Web específica, se encuentran en la carpeta /App_Code del sitio Web.

  - Un proyecto de sitio Web (WSP) genera un archivo ejecutable para cada página Web inteligente. Los archivos ejecutables adicionales se generan a partir de cualquier archivo de código fuente en la carpeta /App_Code.

  - Un proyecto de aplicación web (WAP) genera un único archivo ejecutable que combina el código para todas las páginas Web inteligentes, así como todos los archivos de origen de la carpeta /App_Code.

- El archivo de solución para un proyecto Web se encuentra por separado del propio sitio Web. De forma predeterminada, los archivos de\\la solución se encuentran en la\\sección "Documents and Settings*YourAccount"*(Documentos y configuración de su cuenta) (Mis documentos,\\*\<Visual Studio) *y ">", "Projects*YourWebSite".*

  > [!NOTE]
  > Si desea mantener el archivo de solución con el sitio Web, simplemente muévalo allí y vuelva a abrirlo.

- Si abre un sitio Web que no tiene ningún archivo de solución en Visual Studio, se genera automáticamente un nuevo archivo de solución para él.

- Los proyectos web no tienen archivos de proyecto. La información del proyecto se almacena en el archivo de solución, el archivo web.config y en otro lugar.

- Agregar propiedades globales a un proyecto Web crea automáticamente un archivo de almacenamiento en la carpeta de solución de proyecto web.

- Una página Web inteligente se puede asociar a un lenguaje de \<programación del lado servidor mediante la directiva Page o el script runat-"server"> etiqueta.

- Además, las páginas Web pueden tener cualquier número de bloques de scripting del lado cliente escritos en cualquier lenguaje de scripting.

- Un sistema de proyecto de sitio Web se implementa [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] agregando plantillas de proyecto y elemento y registro al proyecto.

- Un sistema WAP se implementa como un subtipo de proyecto, también llamado sabor del proyecto. El [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] proyecto está aromatizado por el subtipo WAP para crear el sistema WAP. Para obtener más información sobre los subtipos de proyecto, vea [Subtipos de proyecto](../../extensibility/internals/project-subtypes.md).

- Una página Web inteligente combina HTML con un lenguaje de programación del lado servidor. El idioma del lado servidor se denomina idioma contenido. Para admitir un lenguaje contenido, el sistema <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> de proyectos Web debe implementar la familia de interfaces.

  - Para admitir el lenguaje contenido en un editor, el servicio de lenguaje HTML debe aplazar la visualización de código de idioma contenido a un servicio de lenguaje contenido.

  - Los marcadores de error (rotulaciones rojas) siempre deben crearse en el búfer principal del editor de código.

## <a name="see-also"></a>Vea también
- [Proyectos web](../../extensibility/internals/web-projects.md)

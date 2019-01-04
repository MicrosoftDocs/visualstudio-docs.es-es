---
title: Web Essentials del proyecto | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a18ee19755e79c03bb24104cb444af8168307d17
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826577"
---
# <a name="web-project-essentials"></a>Conceptos básicos del proyecto web
Los proyectos Web creación aplicaciones Web. Puede usar un proyecto Web para crear una aplicación Web que tiene páginas Web inteligentes. Una página Web inteligente tiene código de servidor que representa la página Web a petición.  
  
 Con los lenguajes de programación tradicionales, como [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], puede crear las páginas Web inteligentes para recopilar y procesar información de un usuario, almacenarlo en una base de datos y así sucesivamente.  
  
- El modelo de código subyacente asocia los archivos de código fuente dependiente con páginas Web que tiene el archivo .aspx de extensión o .asmx. Por ejemplo, hello.aspx podría tener la hello.aspx.cs de archivo de código fuente dependiente.  
  
- El código de servidor asociado a una página Web inteligente se compila en un archivo ejecutable que se encuentra en la carpeta/bin del sitio Web.  
  
- Archivos de código de origen adicionales, como las clases auxiliares que no están asociados con una página Web específica, se encuentran en la carpeta /bin del sitio Web.  
  
  -   Un proyecto de sitio Web (WSP) genera un archivo ejecutable para cada página Web inteligente. Se generan archivos ejecutables adicionales de los archivos de código fuente en la carpeta /bin.  
  
  -   Un proyecto de aplicación Web (WAP) genera un único archivo ejecutable que combina el código para todas las páginas Web inteligentes, así como todos los archivos de origen en la carpeta /bin.  
  
- El archivo de solución para un proyecto Web se encuentra por separado desde el propio sitio Web. De forma predeterminada, los archivos de solución se encuentran en \Documents and Settings\\*suCuenta*documentos \My\\*\<Visual Studio ### >* \Projects\\ *YourWebSite*.  
  
  > [!NOTE]
  >  Si desea mantener el archivo de solución con el sitio Web, simplemente muévala ahí y vuelva a abrirlo.  
  
- Si abre un sitio Web que no tiene ningún archivo de solución en Visual Studio, se genera automáticamente un nuevo archivo de solución para él.  
  
- Los proyectos Web no tienen ningún archivo de proyecto. Información del proyecto se almacena en el archivo de solución, el archivo web.config y en otros lugares.  
  
- Agregar automáticamente las propiedades globales a un proyecto Web, crea un archivo de almacenamiento en la carpeta de solución de proyecto Web.  
  
- Una página Web inteligente puede asociarse con un lenguaje de programación del lado servidor mediante el uso de la directiva de página o el \<script runat = "server" > etiqueta.  
  
- Además, las páginas Web puede tener cualquier número de bloques de scripting del lado cliente escritas en cualquier lenguaje de scripting.  
  
- Un sistema de proyectos de sitio Web se implementa mediante la adición de plantillas de proyecto y elemento y el registro para el [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] proyecto.  
  
- Un sistema WAP se implementa como un subtipo de proyecto, que también se denomina un tipo de proyecto. El [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] es característico de proyecto para crear el sistema WAP el subtipo de WAP. Para obtener más información sobre los subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
- Una página Web inteligente combina HTML con un lenguaje de programación del lado servidor. El lenguaje de servidor se denomina lenguaje contenido. Para admitir un lenguaje contenido, debe implementar el sistema del proyecto Web el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> familia de interfaces.  
  
  -   Para admitir el lenguaje contenido en un editor, el servicio de lenguaje HTML debe aplazar la visualización de código de lenguaje contenido a un servicio de lenguaje contenido.  
  
  -   Marcadores de error (rojo detectores) siempre deben crearse en el búfer principal del editor de código.  
  
## <a name="see-also"></a>Vea también  
 [Proyectos web](../../extensibility/internals/web-projects.md)
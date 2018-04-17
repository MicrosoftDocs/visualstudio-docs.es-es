---
title: Web Essentials proyecto | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6918c539409a31dfe5249adb5858ca20c8c2337c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="web-project-essentials"></a>Fundamentos de proyecto Web
Proyectos Web crear aplicaciones Web. Puede utilizar un proyecto Web para crear una aplicación Web que tiene páginas Web inteligentes. Una página Web inteligente tiene código de servidor que representa la página Web a petición.  
  
 Con los lenguajes de programación tradicionales, como [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], puede crear páginas Web que inteligente para recopilar y procesar la información de un usuario, almacenarlos en una base de datos y así sucesivamente.  
  
-   El modelo de código subyacente asocia los archivos de código fuente dependiente a páginas Web que tienen el archivo extensión .aspx o .asmx. Por ejemplo, hello.aspx podría tener la hello.aspx.cs de archivo de código fuente dependiente.  
  
-   El código de servidor asociado a una página Web inteligente se compila en un archivo ejecutable que se encuentra en la carpeta/bin del sitio Web.  
  
-   Archivos de código de origen adicionales, como clases auxiliares que no están asociados a una página Web específica, se encuentran en el sitio Web la carpeta.  
  
    -   Un proyecto de sitio Web (WSP) genera un archivo ejecutable para cada página Web inteligente. Archivos ejecutables adicionales se generan a partir de los archivos de código fuente en la carpeta.  
  
    -   Un proyecto de aplicación Web (WAP) produce un solo archivo ejecutable que combina el código para todas las páginas Web inteligentes, así como todos los archivos de origen en la carpeta.  
  
-   El archivo de solución para un proyecto Web se encuentra por separado desde el propio sitio Web. De forma predeterminada, los archivos de solución se encuentran en \Documents and Settings\\*suCuenta*documentos \My\\*\<Visual Studio ### >*\Projects\\ *YourWebSite*.  
  
    > [!NOTE]
    >  Si desea mantener el archivo de solución con el sitio Web, simplemente mueva allí y vuelva a abrirlo.  
  
-   Si abre un sitio Web que no tenga ningún archivo de solución en Visual Studio, se genera automáticamente un nuevo archivo de solución para él.  
  
-   Los proyectos Web no tienen ningún archivo de proyecto. Información del proyecto se almacena en el archivo de solución, el archivo web.config y en otros lugares.  
  
-   Agregar automáticamente las propiedades globales a un proyecto Web, crea un archivo de almacenamiento en la carpeta de solución de proyecto Web.  
  
-   Una página Web inteligente puede asociarse con un lenguaje de programación de servidor mediante la directiva de página o el \<script runat = "server" > etiqueta.  
  
-   Además, las páginas Web puede tener cualquier número de bloques de secuencias de comandos de cliente escrito en cualquier lenguaje de scripting.  
  
-   Un sistema de proyectos de sitio Web se implementa mediante la adición de plantillas de proyecto y elemento y el registro para el [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] proyecto.  
  
-   Un sistema WAP se implementa como un subtipo de proyecto, que también se denomina un tipo de proyecto. El [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] es característico de proyecto por el subtipo WAP para crear el sistema WAP. Para obtener más información sobre subtipos de proyecto, vea [subtipos de proyecto](../../extensibility/internals/project-subtypes.md).  
  
-   Una página Web inteligente combina HTML con un lenguaje de programación de servidor. El idioma de servidor se denomina el lenguaje independiente. Para admitir un lenguaje independiente, debe implementar el sistema del proyecto Web el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> familia de interfaces.  
  
    -   Para admitir el idioma contenido en un editor, el servicio de lenguaje HTML debe aplazar muestran código de idioma independiente para un servicio de lenguaje independiente.  
  
    -   Marcadores de error (detectores rojos) siempre deben crearse en el búfer principal del editor de código.  
  
## <a name="see-also"></a>Vea también  
 [Proyectos web](../../extensibility/internals/web-projects.md)
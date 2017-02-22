---
title: "C&#243;mo: Editar archivos XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# C&#243;mo: Editar archivos XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Editor XML es el nuevo editor de archivos XML.Se puede utilizar en un archivo XML independiente o en uno asociado con un proyecto de Visual Studio.El Editor XML está asociado con las siguientes extensiones de archivo: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt y .vssettings.También está asociado con otros tipos de archivos que no tengan registrado un editor específico y que incluyan contenido XML o DTD.  
  
> [!NOTE]
>  Los documentos XHTML son manejados con el Editor HTML.  
  
### Para editar un archivo XML  
  
1.  Haga doble clic en el archivo que desea editar.  
  
### Para agregar un nuevo archivo XML a un proyecto  
  
1.  En el menú **Proyecto**, seleccione **Agregar nuevo elemento**.  
  
2.  Seleccione **Archivo XML** en el panel **Plantillas**.  
  
3.  Escriba el nombre de archivo en el campo **Nombre** y presione **Agregar**.  
  
     Se agrega el archivo XML al proyecto y se abre en el Editor XML.El archivo contiene la declaración XML predeterminada, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### Para agregar un archivo XML existente a un proyecto  
  
1.  En el menú **Proyecto**, seleccione **Agregar elemento existente**.  
  
     Aparece el cuadro de diálogo **Agregar elemento existente**.  
  
2.  Seleccione un archivo XML y presione **Agregar**.  
  
### Para crear un nuevo archivo XML o XSLT  
  
1.  En el menú **Archivo**, seleccione **Nuevo**.  
  
     Aparece el cuadro de diálogo **Nuevo archivo**.  
  
2.  Seleccione **Archivo XML** para crear un nuevo archivo XML, o seleccione **Archivo XSLT** para crear una nueva hoja de estilos XSLT.  
  
3.  Haga clic en **Abrir**.  
  
### Para crear un proyecto de archivos XML  
  
1.  En el menú **Archivo**, seleccione **Nuevo** y haga clic en **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
2.  Seleccione el lenguaje de código de su elección, seleccione **Proyecto vacío** y haga clic en **Aceptar**.  
  
3.  Agregue archivos XML al proyecto.  
  
     El Editor XML busca los esquemas que agregue a este proyecto y los utiliza para la validación e IntelliSense en cualquier archivo XML, de esquema o XSLT que edite mientras este proyecto está abierto.  
  
## Vea también  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Propiedades de documentos XML, Ventana Propiedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Cómo: Crear un esquema XML a partir de un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)
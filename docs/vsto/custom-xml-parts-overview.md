---
title: "Informaci&#243;n general sobre los elementos XML personalizados | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "elementos XML personalizados [desarrollo de Office en Visual Studio]"
  - "elementos XML personalizados [desarrollo de Office en Visual Studio], acerca de"
  - "datos [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "documentos [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "incrustar datos XML en documentos [desarrollo de Office en Visual Studio]"
  - "Excel [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "documentos de Office [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "formatos Office Open XML [desarrollo de Office en Visual Studio]"
  - "Word [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "XML [desarrollo de Office en Visual Studio], elementos XML personalizados"
  - "formatos de archivo XML [desarrollo de Office en Visual Studio]"
  - "elementos XML [desarrollo de Office en Visual Studio]"
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Informaci&#243;n general sobre los elementos XML personalizados
  Puede insertar datos XML en documentos para algunas aplicaciones de Microsoft Office.  Al insertar datos XML en un documento, los datos se llaman *elementos XML personalizados*.  
  
 Puede crear y modificar elementos XML personalizados en un documento mediante un complemento de VSTO o una solución de nivel de documento en Visual Studio.  No es necesario iniciar la aplicación de Microsoft Office para crear y modificar elementos XML personalizados.  
  
 **Aplicación:** la información de este tema se aplica a los proyectos de nivel de documento y a los proyectos de complemento de VSTO para Excel, PowerPoint y Word.  Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio también permite almacenar en memoria caché objetos de datos en las personalizaciones de nivel de documento.  Esta característica difiere de los elementos XML personalizados, aunque hay algunas similitudes.  Para obtener más información, consulte [Datos almacenados en caché en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## Descripción de los elementos XML personalizados  
 Los elementos XML personalizados se introdujeron en 2007 Microsoft Office System, junto con los formatos Open XML.  Estos formatos incluyen nuevos formatos de archivo basados en XML para Excel, PowerPoint y Word \(como .xlsx, .pptx y .docx\).  Los documentos en estos formatos constan de archivos XML \(también llamados *elementos XML*\) que se organizan en carpetas en un archivo ZIP.  La mayoría de los elementos XML son elementos integrados que ayudan a definir la estructura y el estado del documento.  Sin embargo, los documentos también pueden contener elementos XML personalizados, que puede usar para almacenar datos XML arbitrarios en los documentos.  
  
 Los formatos de archivo XML permiten que las aplicaciones trabajen con documentos de maneras que no son posibles con los formatos de archivo binario anteriores \(como .xls, .ppt y .doc\).  Cualquier aplicación que pueda leer archivos ZIP puede examinar y modificar el contenido de los documentos, incluso si no está instalado Microsoft Office.  
  
 Para obtener más información sobre la estructura de Open XML y elementos XML personalizados, consulte los siguientes artículos:  
  
-   [Introducción a los formatos de archivo XML abiertos de Office \(2007\)](http://msdn.microsoft.com/es-es/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Cómo: Manipular documentos con formatos Open XML](http://msdn.microsoft.com/es-es/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Tutorial: Formato XML de Word 2007](http://msdn.microsoft.com/es-es/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Compilar documentos de Word 2007 con formatos Open XML](http://msdn.microsoft.com/es-es/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word y PowerPoint también permiten usar elementos XML personalizados en documentos guardados en los formatos de archivo binario.  Sin embargo, si se guarda un documento en un formato binario, no se puede agregar o modificar elementos XML personalizados sin iniciar la aplicación de Microsoft Office.  
  
## Crear y modificar elementos XML personalizados  
 Puede crear o modificar elementos XML personalizados cuando el documento está abierto en la aplicación de Office o cuando está cerrado, incluso si no está instalado Microsoft Office.  
  
### Modificar elementos XML mientras se ejecuta la aplicación de Office  
 Puede trabajar con elementos XML personalizados usando una personalización de nivel de documento o un complemento de VSTO.  Si está usando una personalización de nivel de documento, normalmente trabajará con elementos XML personalizados que se encuentran en el documento personalizado.  Si está usando un complemento de VSTO, puede crear o modificar elementos XML personalizados en cualquier documento que esté abierto en la aplicación.  
  
 Para crear un elemento XML personalizado con Visual Studio, agregue un nuevo <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del documento.  Para obtener más información, vea los temas siguientes:  
  
-   [Cómo: Agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### Modificar elementos XML sin iniciar la aplicación de Office  
 Puede agregar o modificar un elemento XML personalizado sin iniciar Excel, PowerPoint o Word.  Esto es útil si desea trabajar con datos XML en un documento en un equipo que no tiene instaladas aplicaciones de Microsoft Office, como un servidor.  
  
 Para agregar un elemento XML personalizado sin iniciar Microsoft Office, use las clases del SDK de Open XML.  Estas clases están diseñadas para proporcionar acceso a contenido de Open XML específico de documentos de Office.  Por ejemplo, para agregar un elemento XML personalizado a un libro de Excel, use el método [AddNewPart\<T\>](http://msdn.microsoft.com/es-es/47c348c0-77ab-a504-5097-bcd6a213921a) de un objeto [WorkbookPart](http://msdn.microsoft.com/es-es/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2).  Para obtener más información, consulte [SDK 2.0 de Open XML](http://msdn.microsoft.com/es-es/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## Enlazar elementos XML personalizados a controles de contenido de Word  
 Puede enlazar controles de contenido en una solución de Word a los elementos de un elemento XML personalizado.  Cuando se enlaza un control de contenido a un elemento XML personalizado, los datos del elemento XML personalizado se muestran en la interfaz de usuario \(IU\) del control de contenido.  Si un usuario edita el texto del control, el elemento XML correspondiente se actualiza automáticamente.  De igual forma, si se modifican los valores de los elementos XML personalizados, los controles de contenido que están enlazados a los elementos XML muestran los nuevos datos.  Para obtener más información, consulte [Controles de contenido](../vsto/content-controls.md).  
  
## Vea también  
 [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Cómo: Agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Tutorial: Enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  
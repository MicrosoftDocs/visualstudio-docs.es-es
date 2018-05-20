---
title: Información general sobre elementos XML personalizados
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e99e64de135ab46baf40a959986c041538c09593
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="custom-xml-parts-overview"></a>Información general sobre elementos XML personalizados
  Puede insertar datos XML en documentos para algunas aplicaciones de Microsoft Office. Al incrustar datos XML en un documento, los datos se denominan un *elemento XML personalizado*.  
  
 Puede crear y modificar elementos XML personalizados en un documento mediante un complemento de VSTO o una solución de nivel de documento en Visual Studio. No es necesario iniciar la aplicación de Microsoft Office para crear y modificar elementos XML personalizados.  
  
 **Se aplica a:** la información de este tema se aplica a los proyectos de nivel de documento y los proyectos de complemento de VSTO para Excel, PowerPoint y Word. Para obtener más información, consulte [características disponibles por tipo de aplicación y el proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio también permite almacenar en memoria caché objetos de datos en las personalizaciones de nivel de documento. Esta característica difiere de los elementos XML personalizados, aunque hay algunas similitudes. Para obtener más información, consulte [datos en las personalizaciones de nivel de documento en caché](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Comprender los elementos XML personalizados  
 Los elementos XML personalizados se introdujeron en 2007 Microsoft Office System, junto con los formatos Open XML. Estos formatos incluyen nuevos formatos de archivo basado en XML para Excel, PowerPoint y Word (como *.xlsx*, *.pptx*, y *.docx*). Documentos en estos formatos constan de archivos XML (también denominada *elementos XML*) que se organizan en carpetas en un archivo ZIP. La mayoría de los elementos XML son elementos integrados que ayudan a definir la estructura y el estado del documento. Sin embargo, los documentos también pueden contener elementos XML personalizados, que puede usar para almacenar datos XML arbitrarios en los documentos.  
  
 Formatos de archivo XML permiten a las aplicaciones para trabajar con documentos de maneras que no son posibles con los formatos de archivo binario anteriores (como *.xls*, *.ppt*, y *.doc*). Cualquier aplicación que pueda leer archivos ZIP puede examinar y modificar el contenido de los documentos, incluso si no está instalado Microsoft Office.  
  
 Para obtener más información sobre la estructura de Open XML y elementos XML personalizados, consulte los siguientes artículos:  
  
-   [Introducción a los formatos de archivo de Office (2007) Open XML](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Cómo: manipular documentos con formatos Open XML](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Tutorial: Formato de XML de Word 2007](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Creación de documentos de Word 2007 con formatos Open XML](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word y PowerPoint también permiten usar elementos XML personalizados en documentos guardados en los formatos de archivo binario. Sin embargo, si se guarda un documento en un formato binario, no se puede agregar o modificar elementos XML personalizados sin iniciar la aplicación de Microsoft Office.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Crear y modificar elementos XML personalizados  
 Puede crear o modificar elementos XML personalizados cuando el documento está abierto en la aplicación de Office o cuando está cerrado, incluso si no está instalado Microsoft Office.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modificar elementos XML mientras se ejecuta la aplicación de Office  
 Puede trabajar con elementos XML personalizados usando una personalización de nivel de documento o un complemento de VSTO. Si está usando una personalización de nivel de documento, normalmente trabajará con elementos XML personalizados que se encuentran en el documento personalizado. Si está usando un complemento de VSTO, puede crear o modificar elementos XML personalizados en cualquier documento que esté abierto en la aplicación.  
  
 Para crear un elemento XML personalizado con Visual Studio, agregue un nuevo <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del documento. Para obtener más información, vea los temas siguientes:  
  
-   [Cómo: agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Cómo: agregar elementos XML personalizados a documentos mediante complementos VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modificar elementos XML sin iniciar la aplicación de Office  
 Puede agregar o modificar un elemento XML personalizado sin iniciar Excel, PowerPoint o Word. Esto es útil si desea trabajar con datos XML en un documento en un equipo que no tiene instaladas aplicaciones de Microsoft Office, como un servidor.  
  
 Para agregar un elemento XML personalizado sin iniciar Microsoft Office, use las clases del SDK de Open XML. Estas clases están diseñadas para proporcionar acceso a contenido de Open XML específico de documentos de Office. Por ejemplo, para agregar un elemento XML personalizado a un libro de Excel, use la [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a) método de un [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) objeto. Para obtener más información, consulte [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Enlazar elementos XML personalizados a controles de contenido de Word  
 Puede enlazar controles de contenido en una solución de Word a los elementos de un elemento XML personalizado. Cuando se enlaza un control de contenido a un elemento XML personalizado, los datos del elemento XML personalizado se muestran en la interfaz de usuario (IU) del control de contenido. Si un usuario edita el texto del control, el elemento XML correspondiente se actualiza automáticamente. De igual forma, si se modifican los valores de los elementos XML personalizados, los controles de contenido que están enlazados a los elementos XML muestran los nuevos datos. Para obtener más información, consulte [controles de contenido](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Esquemas XML y los datos en las personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Cómo: agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Cómo: agregar elementos XML personalizados a documentos mediante complementos VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Tutorial: Enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  
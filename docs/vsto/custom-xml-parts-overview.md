---
title: Información general sobre elementos XML personalizados
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4906bfc091f9fe59b2f7c64d3000deba8018c5f6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862140"
---
# <a name="custom-xml-parts-overview"></a>Información general sobre elementos XML personalizados
  Puede insertar datos XML en documentos para algunas aplicaciones de Microsoft Office. Al incrustar datos XML en un documento, los datos se denominan un *elemento XML personalizado*.  
  
 Puede crear y modificar elementos XML personalizados en un documento mediante un complemento de VSTO o una solución de nivel de documento en Visual Studio. No es necesario iniciar la aplicación de Microsoft Office para crear y modificar elementos XML personalizados.  
  
 **Se aplica a:** La información de este tema se aplica a los proyectos de nivel de documento y los proyectos de complemento VSTO para Excel, PowerPoint y Word. Para obtener más información, consulte [características disponibles por tipo de aplicación y el proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio también permite almacenar en memoria caché objetos de datos en las personalizaciones de nivel de documento. Esta característica difiere de los elementos XML personalizados, aunque hay algunas similitudes. Para obtener más información, consulte [en caché los datos en las personalizaciones de nivel de documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understand-custom-xml-parts"></a>Comprender los elementos XML personalizados  
 Los elementos XML personalizados se introdujeron en 2007 Microsoft Office System, junto con los formatos Open XML. Estos formatos incluyen nuevos formatos de archivo basado en XML para Excel, PowerPoint y Word (como *.xlsx*, *.pptx*, y *.docx*). Los documentos en estos formatos constan de archivos XML (también denominado *elementos XML*) que se organizan en carpetas en un archivo ZIP. La mayoría de los elementos XML son elementos integrados que ayudan a definir la estructura y el estado del documento. Sin embargo, los documentos también pueden contener elementos XML personalizados, que puede usar para almacenar datos XML arbitrarios en los documentos.  
  
 El archivo XML da formato a las aplicaciones para trabajar con documentos de maneras que no son posibles con los formatos de archivo binario anteriores (como *.xls*, *.ppt*, y *.doc*). Cualquier aplicación que pueda leer archivos ZIP puede examinar y modificar el contenido de los documentos, incluso si no está instalado Microsoft Office.  
  
 Para obtener más información sobre la estructura de Open XML y elementos XML personalizados, consulte los siguientes artículos:  
  
-   [Introducción a los formatos de archivo de Office (2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))  
  
-   [Cómo: Manipular documentos con formatos XML abiertos](/previous-versions/office/developer/office-2007/aa982683(v=office.12))  
  
-   [Tutorial: Formato XML de Word 2007](/previous-versions/office/developer/office-2007/bb266220(v=office.12))  
  
-   [Creación de documentos de Word 2007 con formatos XML abiertos](/previous-versions/office/developer/office-2007/bb264572(v=office.12))  
  
> [!NOTE]  
>  Excel, Word y PowerPoint también permiten usar elementos XML personalizados en documentos guardados en los formatos de archivo binario. Sin embargo, si se guarda un documento en un formato binario, no se puede agregar o modificar elementos XML personalizados sin iniciar la aplicación de Microsoft Office.  
  
## <a name="create-and-modify-custom-xml-parts"></a>Crear y modificar elementos XML personalizados  
 Puede crear o modificar elementos XML personalizados cuando el documento está abierto en la aplicación de Office o cuando está cerrado, incluso si no está instalado Microsoft Office.  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Modificar elementos XML mientras se ejecuta la aplicación de Office  
 Puede trabajar con elementos XML personalizados mediante el uso de una personalización de nivel de documento o un complemento de VSTO. Si está usando una personalización de nivel de documento, normalmente trabajará con elementos XML personalizados que se encuentran en el documento personalizado. Si usas un complemento de VSTO, puede crear o modificar elementos XML personalizados en cualquier documento que está abierto en la aplicación.  
  
 Para crear un elemento XML personalizado con Visual Studio, agregue un nuevo <xref:Microsoft.Office.Core.CustomXMLPart> a la colección <xref:Microsoft.Office.Core.CustomXMLParts> del documento. Para obtener más información, vea los temas siguientes:  
  
-   [Cómo: Agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Modificar elementos XML sin iniciar la aplicación de Office  
 Puede agregar o modificar un elemento XML personalizado sin iniciar Excel, PowerPoint o Word. Esto es útil si desea trabajar con datos XML en un documento en un equipo que no tiene instaladas aplicaciones de Microsoft Office, como un servidor.  
  
 Para agregar un elemento XML personalizado sin iniciar Microsoft Office, use las clases del SDK de Open XML. Estas clases están diseñadas para proporcionar acceso a contenido de Open XML específico de documentos de Office. Por ejemplo, para agregar un elemento XML personalizado a un libro de Excel, use el <xref:DocumentFormat.OpenXml.Packaging.OpenXmlPartContainer.AddNewPart%2A> método de un <xref:DocumentFormat.OpenXml.Packaging.WorkbookPart> objeto. Para obtener más información, consulte [Open XML SDK](/office/open-xml/open-xml-sdk).  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>Enlazar elementos XML personalizados a controles de contenido de Word  
 Puede enlazar controles de contenido en una solución de Word a los elementos de un elemento XML personalizado. Cuando se enlaza un control de contenido a un elemento XML personalizado, los datos del elemento XML personalizado se muestran en la interfaz de usuario (IU) del control de contenido. Si un usuario edita el texto del control, el elemento XML correspondiente se actualiza automáticamente. De igual forma, si se modifican los valores de los elementos XML personalizados, los controles de contenido que están enlazados a los elementos XML muestran los nuevos datos. Para obtener más información, consulte [controles de contenido](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Vea también  
 [Esquemas y datos en las personalizaciones de nivel de documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Cómo: Agregar elementos XML personalizados a personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Cómo: Agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Controles de contenido](../vsto/content-controls.md)   
 [Tutorial: Enlazar controles de contenido a elementos XML personalizados](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  

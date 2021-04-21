---
title: 'Cómo: Crear nuevos documentos de Visio mediante programación'
description: Obtenga información sobre cómo puede crear mediante programación un nuevo documento de dibujo de Microsoft Visio y agregarlo a la colección Documentos de documentos abiertos de Visio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4b12b7e94109391928ad7c83387917e5934ae1c7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825321"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Cómo: Crear nuevos documentos de Visio mediante programación
  Cuando se crea un nuevo documento de dibujo de Visio de Microsoft Office, debe agregarse a la colección `Microsoft.Office.Interop.Visio.Documents` de documentos de Visio abiertos. Por consiguiente, el método `Microsoft.Office.Interop.Visio.Documents.Add` crea un nuevo documento de dibujo de Visio. Para obtener más información, consulte la documentación de referencia VBA para el método [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .

## <a name="create-new-blank-documents"></a>Creación de nuevos documentos en blanco

### <a name="to-create-a-new-document"></a>Para crear un nuevo documento

- Use el método `Microsoft.Office.Interop.Visio.Documents.Add` para crear un nuevo documento en blanco que no se base en una plantilla.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Creación de documentos copiados de documentos existentes
 El método `Microsoft.Office.Interop.Visio.Documents.Add` puede crear un documento nuevo que es una copia de un documento de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa del diagrama.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Para crear un documento nuevo copiado de uno existente

- Llame al método `Microsoft.Office.Interop.Visio.Documents.Add` y especifique la ruta de acceso del diagrama de Visio.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Creación de galerías de símbolos copiadas de galerías de símbolos existentes
 El método [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) puede crear una nueva galería de símbolos que sea una copia de una galería de símbolos de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la galería de símbolos.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Para crear una galería de símbolos nueva copiada de una existente

- Llame al método `Microsoft.Office.Interop.Visio.Documents.Add` y especifique la ruta de acceso de la galería de símbolos.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Creación de documentos basados en plantillas existentes
 El método puede crear un nuevo documento `Microsoft.Office.Interop.Visio.Documents.Add` (un *archivo .vsd)* basado en una plantilla de Visio existente (un *archivo .vst).* Este método copia las galerías de símbolos, estilos y configuraciones que forman parte del área de trabajo de la plantilla. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Para crear un documento nuevo basado en una plantilla existente

- Llame al método `Microsoft.Office.Interop.Visio.Documents.Add` y especifique la ruta de acceso de la plantilla.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Compilar el código
 Para este ejemplo de código se necesita lo siguiente:

- Un documento de Visio denominado debe encontrarse en un directorio denominado en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta `myDrawing.vsd` `Test` *Documentos* (para Windows Vista). 

- Un documento de Visio denominado debe encontrarse en un directorio denominado en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta `myStencil.vss` `Test` *Documentos* (para Windows Vista). 

- Un documento de Visio denominado debe encontrarse en un directorio denominado en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta `myTemplate.vst` `Test` *Documentos* (para Windows Vista). 

## <a name="see-also"></a>Consulte también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Introducción al modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)
- [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)
- [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)
- [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)

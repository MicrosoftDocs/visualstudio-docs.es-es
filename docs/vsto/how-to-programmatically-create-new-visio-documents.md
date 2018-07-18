---
title: 'Cómo: crear nuevos documentos de Visio mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9b5b66690d3856a2bf1fc6df417b60ab5e293127
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256749"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Cómo: crear nuevos documentos de Visio mediante programación
  Cuando se crea un nuevo Microsoft Office Visio documento de dibujo, debe agregarse a la `Microsoft.Office.Interop.Visio.Documents` colección de documentos de Visio abiertos. Por lo tanto, el `Microsoft.Office.Interop.Visio.Documents.Add` método crea un nuevo documento de dibujo de Visio. Para obtener más información, consulte la documentación de referencia VBA para el método [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="create-new-blank-documents"></a>Crear nuevos documentos en blanco  
  
### <a name="to-create-a-new-document"></a>Para crear un nuevo documento  
  
-   Use el `Microsoft.Office.Interop.Visio.Documents.Add` método para crear un nuevo documento en blanco que no se basa en una plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Crear documentos copiados de documentos existentes  
 El `Microsoft.Office.Interop.Visio.Documents.Add` método puede crear un documento nuevo que es una copia de un documento de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa del diagrama.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Para crear un documento nuevo copiado de uno existente  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Documents.Add` método y especifique la ruta de acceso del diagrama de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Crear galerías de símbolos copiadas de otras existentes  
 El método [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) puede crear una nueva galería de símbolos que sea una copia de una galería de símbolos de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la galería de símbolos.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Para crear una galería de símbolos nueva copiada de una existente  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Documents.Add` método y especifique la ruta de acceso de la Galería de símbolos.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Crear documentos basados en plantillas existentes  
 El `Microsoft.Office.Interop.Visio.Documents.Add` método puede crear un nuevo documento (un *.vsd* archivo) que se basa en una plantilla de Visio existente (una *.vst* archivo). Este método copia las galerías de símbolos, estilos y configuraciones que forman parte del área de trabajo de la plantilla. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Para crear un documento nuevo basado en una plantilla existente  
  
-   Llame a la `Microsoft.Office.Interop.Visio.Documents.Add` método y especifique la ruta de acceso de la plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Compile el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un documento de Visio denominado `myDrawing.vsd` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
-   Un documento de Visio denominado `myStencil.vss` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
-   Un documento de Visio denominado `myTemplate.vst` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  
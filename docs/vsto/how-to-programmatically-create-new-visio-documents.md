---
title: Procedimiento Crear nuevos documentos de Visio mediante programación
ms.date: 02/02/2017
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
ms.openlocfilehash: 0962c0d7927fd7b21969b36020e2a40d587cf452
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872510"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Procedimiento Crear nuevos documentos de Visio mediante programación
  Cuando se crea un nuevo documento de dibujo de Visio de Microsoft Office, debe agregarse a la colección `Microsoft.Office.Interop.Visio.Documents` de documentos de Visio abiertos. Por consiguiente, el método `Microsoft.Office.Interop.Visio.Documents.Add` crea un nuevo documento de dibujo de Visio. Para obtener más información, consulte la documentación de referencia VBA para el método [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) .  
  
## <a name="create-new-blank-documents"></a>Crear nuevos documentos en blanco  
  
### <a name="to-create-a-new-document"></a>Para crear un nuevo documento  
  
-   Use el método `Microsoft.Office.Interop.Visio.Documents.Add` para crear un nuevo documento en blanco que no se base en una plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="create-documents-copied-from-existing-documents"></a>Crear documentos copiados de documentos existentes  
 El método `Microsoft.Office.Interop.Visio.Documents.Add` puede crear un documento nuevo que es una copia de un documento de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa del diagrama.  
  
### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Para crear un documento nuevo copiado de uno existente  
  
-   Llame al método `Microsoft.Office.Interop.Visio.Documents.Add` y especifique la ruta de acceso del diagrama de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="create-stencils-copied-from-existing-stencils"></a>Crear galerías de símbolos copiadas de otras existentes  
 El método [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) puede crear una nueva galería de símbolos que sea una copia de una galería de símbolos de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la galería de símbolos.  
  
### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Para crear una galería de símbolos nueva copiada de una existente  
  
-   Llame al método `Microsoft.Office.Interop.Visio.Documents.Add` y especifique la ruta de acceso de la galería de símbolos.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="create-documents-based-on-existing-templates"></a>Crear documentos basados en plantillas existentes  
 El `Microsoft.Office.Interop.Visio.Documents.Add` método puede crear un nuevo documento (un *.vsd* archivo) que se basa en una plantilla de Visio existente (una *.vst* archivo). Este método copia las galerías de símbolos, estilos y configuraciones que forman parte del área de trabajo de la plantilla. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.  
  
### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Para crear un documento nuevo basado en una plantilla existente  
  
-   Llame al método `Microsoft.Office.Interop.Visio.Documents.Add` y especifique la ruta de acceso de la plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un documento de Visio denominado `myDrawing.vsd` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
-   Un documento de Visio denominado `myStencil.vss` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
-   Un documento de Visio denominado `myTemplate.vst` debe estar ubicado en un directorio denominado `Test` en el *Mis documentos* carpeta (para Windows XP y versiones anteriores) o la *documentos* carpeta (para Windows Vista).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: Abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: Cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: Guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  

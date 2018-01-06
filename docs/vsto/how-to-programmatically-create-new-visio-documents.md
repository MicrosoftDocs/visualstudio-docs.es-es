---
title: "Cómo: crear nuevos documentos de Visio mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
ms.assetid: a0294d4c-be49-4cd0-b22e-3ec7568f3ec7
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3f96738d9e553ede2b74ebc118a2769b32926cba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Cómo: Crear nuevos documentos de Visio mediante programación
  Cuando se crea una nueva Microsoft Office Visio documento de dibujo, agregarlo a la colección Microsoft.Office.Interop.Visio.Documents de documentos de Visio abiertos. Por consiguiente, el método Microsoft.Office.Interop.Visio.Documents.Add crea un nuevo documento de dibujo de Visio. Para obtener más información, consulte la documentación de referencia VBA para el método [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) .  
  
## <a name="creating-new-blank-documents"></a>Crear nuevos documento en blanco  
  
#### <a name="to-create-a-new-document"></a>Para crear un nuevo documento  
  
-   Utilice el método Microsoft.Office.Interop.Visio.Documents.Add para crear un nuevo documento en blanco que no se basa en una plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]  
  
## <a name="creating-documents-copied-from-existing-documents"></a>Crear documentos copiados de documentos existentes  
 El método Microsoft.Office.Interop.Visio.Documents.Add puede crear un documento nuevo que es una copia de un documento de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa del diagrama.  
  
#### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Para crear un documento nuevo copiado de uno existente  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Add y especifique la ruta de acceso del diagrama de Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]  
  
## <a name="creating-stencils-copied-from-existing-stencils"></a>Crear galerías de símbolos copiadas de otras existentes  
 El método [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) puede crear una nueva galería de símbolos que sea una copia de una galería de símbolos de Visio existente. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la galería de símbolos.  
  
#### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Para crear una galería de símbolos nueva copiada de una existente  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Add y especifique la ruta de acceso de la Galería de símbolos.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="creating-documents-based-on-existing-templates"></a>Crear documentos basados en plantillas existentes  
 El método Microsoft.Office.Interop.Visio.Documents.Add puede crear un nuevo documento (un archivo .vsd) que se basa en una plantilla existente de Visio (archivo .vst). Este método copia las galerías de símbolos, estilos y configuraciones que forman parte del área de trabajo de la plantilla. Debe proporcionar el nombre de archivo y la ruta de acceso completa de la plantilla.  
  
#### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Para crear un documento nuevo basado en una plantilla existente  
  
-   Llame al método Microsoft.Office.Interop.Visio.Documents.Add y especifique la ruta de acceso de la plantilla.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo de código se necesita lo siguiente:  
  
-   Un documento de Visio denominado `myDrawing.vsd` debe encontrarse en un directorio denominado `Test` en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta Documentos (para Windows Vista).  
  
-   Un documento de Visio denominado `myStencil.vss` debe encontrarse en un directorio denominado `Test` en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta Documentos (para Windows Vista).  
  
-   Un documento de Visio denominado `myTemplate.vst` debe encontrarse en un directorio denominado `Test` en la carpeta Mis documentos (para Windows XP y versiones anteriores) o en la carpeta Documentos (para Windows Vista).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Información general del modelo de objetos de Visio](../vsto/visio-object-model-overview.md)   
 [Cómo: abrir documentos de Visio mediante programación](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Cómo: cerrar documentos de Visio mediante programación](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Cómo: guardar documentos de Visio mediante programación](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Cómo: Imprimir documentos de Visio mediante programación](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  
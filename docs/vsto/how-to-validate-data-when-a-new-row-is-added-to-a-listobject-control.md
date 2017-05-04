---
title: "C&#243;mo: Validar datos cuando se agrega una fila nueva a un control ListObject | Microsoft Docs"
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
  - "controles [desarrollo de Office en Visual Studio], validación de datos"
  - "Control ListObject, fila nueva"
  - "Control ListObject, validar datos"
ms.assetid: 107bce92-e5ef-40be-8c05-cd6861d39d75
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# C&#243;mo: Validar datos cuando se agrega una fila nueva a un control ListObject
  Los usuarios pueden agregar filas nuevas a un control <xref:Microsoft.Office.Tools.Excel.ListObject> enlazado a datos. Puede validar los datos del usuario antes de confirmar los cambios al origen de datos.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Validación de datos  
 Cada vez que se agrega una fila a un <xref:Microsoft.Office.Tools.Excel.ListObject> que está enlazado a datos, se produce el evento <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow>. Puede controlar este evento para realizar la validación de datos. Por ejemplo, si la aplicación requiere que solo los empleados de edades comprendidas entre 18 y 65 puedan agregarse al origen de datos, puede comprobar que la edad escrita se encuentra dentro de ese intervalo antes de agregar la fila.  
  
> [!NOTE]  
>  Debe comprobar siempre las entradas de los usuarios en el servidor, además del cliente. Para obtener más información, consulta [Aplicaciones cliente seguras](http://msdn.microsoft.com/library/6239592e-fa7d-4dea-9f00-d296d0048b01).  
  
#### Para validar datos cuando se agrega una fila nueva a un control ListObject enlazado a datos  
  
1.  Cree variables para el identificador y <xref:System.Data.DataTable> en el nivel de clase.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#8)]  
  
2.  Cree un nuevo <xref:System.Data.DataTable> y agregue columnas de ejemplo y datos en el controlador de eventos `Startup` de la clase `Sheet1` \(en un proyecto de nivel de documento\) o una clase `ThisAddIn` \(en un proyecto de complemento de VSTO\).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#9)]  
  
3.  Agregue código al controlador de eventos `list1_BeforeAddDataBoundRow` para comprobar si la edad escrita está dentro del intervalo aceptable.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#10)]  
  
## Compilar el código  
 Este ejemplo de código supone que dispone de un <xref:Microsoft.Office.Tools.Excel.ListObject> existente denominado `list1` en la hoja de cálculo en la que aparece este código.  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject &#40;Control&#41;](../vsto/listobject-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cómo: Asignar columnas ListObject a datos](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  
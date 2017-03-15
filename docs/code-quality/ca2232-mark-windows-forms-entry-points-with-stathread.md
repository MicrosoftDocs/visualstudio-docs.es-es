---
title: "CA2232: Marcar puntos de entrada de Windows Forms con STAThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2232: Marcar puntos de entrada de Windows Forms con STAThread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|Identificador de comprobación|CA2232|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Un ensamblado hace referencia al espacio de nombres <xref:System.Windows.Forms> y su punto de entrada no está marcado con el atributo <xref:System.STAThreadAttribute?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.STAThreadAttribute> indica que el modelo de subprocesos de COM para la aplicación es un contenedor uniproceso.  Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente.  Si el atributo no está presente, la aplicación utiliza el modelo de apartamento multiproceso, que no es compatible con Formularios Windows Forms.  
  
> [!NOTE]
>  Los proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] que utilizan el marco de trabajo de la aplicación no tienen que marcar el método **Main** con STAThread.  El compilador [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] lo hace automáticamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el atributo <xref:System.STAThreadAttribute> al punto de entrada.  Si el atributo <xref:System.MTAThreadAttribute?displayProperty=fullName> está presente, quítelo.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si está desarrollando para .NET Compact Framework, para el que el atributo <xref:System.STAThreadAttribute> no es necesario y ni compatible.  
  
## Ejemplo  
 Los ejemplos siguientes muestran el uso correcto de <xref:System.STAThreadAttribute>.  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
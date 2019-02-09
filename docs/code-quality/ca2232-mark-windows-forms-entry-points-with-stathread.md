---
title: 'CA2232: Marcar puntos de entrada de Windows Forms con STAThread'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1bea8ee43c90c0e6559846bad00b61ec434ec46f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923465"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Marcar puntos de entrada de Windows Forms con STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|Identificador de comprobación|CA2232|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Hace referencia un ensamblado el <xref:System.Windows.Forms> espacio de nombres y su punto de entrada no está marcado con el <xref:System.STAThreadAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.STAThreadAttribute> indica que el modelo para la aplicación de subprocesos COM es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente. Si el atributo no está presente, la aplicación utiliza el modelo de apartamento multiproceso, que no es compatible con Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] los proyectos que usan el marco de aplicación no es necesario que marcar el **Main** método con STAThread. El [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador lo hace automáticamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el <xref:System.STAThreadAttribute> atributo al punto de entrada. Si el <xref:System.MTAThreadAttribute?displayProperty=fullName> atributo está presente, quítelo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si está desarrollando para .NET Compact Framework, para que el <xref:System.STAThreadAttribute> atributo es necesario y no se admite.

## <a name="example"></a>Ejemplo
 Los ejemplos siguientes muestran el uso correcto de <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
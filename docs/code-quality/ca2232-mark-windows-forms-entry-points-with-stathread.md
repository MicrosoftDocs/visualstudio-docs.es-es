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
ms.openlocfilehash: dd3f5b76015a3a54ee085b5cc2dd532920ff0795
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920175"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Marcar puntos de entrada de Windows Forms con STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|Identificador de comprobación|CA2232|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
Un ensamblado hace <xref:System.Windows.Forms> referencia al espacio de nombres y su punto de entrada no <xref:System.STAThreadAttribute?displayProperty=fullName> está marcado con el atributo.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.STAThreadAttribute>indica que el modelo de subprocesos COM de la aplicación es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente. Si el atributo no está presente, la aplicación utiliza el modelo de Apartamento multiproceso, que no se admite para Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]los proyectos que usan el marco de trabajo de la aplicación no tienen que marcar el método **Main** con STAThread. El [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador lo hace automáticamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, agregue <xref:System.STAThreadAttribute> el atributo al punto de entrada. Si el <xref:System.MTAThreadAttribute?displayProperty=fullName> atributo está presente, quítelo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si está desarrollando para el .NET Compact Framework, para el que el <xref:System.STAThreadAttribute> atributo no es necesario y no se admite.

## <a name="example"></a>Ejemplo
En los siguientes ejemplos se muestra el uso <xref:System.STAThreadAttribute>correcto de:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
---
title: 'CA2232: marca Windows Forms puntos de entrada con STAThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662792"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Marcar puntos de entrada de Windows Forms con STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|Identificador de comprobación|CA2232|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Un ensamblado hace referencia al espacio de nombres <xref:System.Windows.Forms> y su punto de entrada no está marcado con el atributo <xref:System.STAThreadAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.STAThreadAttribute> indica que el modelo de subprocesos COM de la aplicación es un contenedor uniproceso. Este atributo debe estar presente en el punto de entrada de cualquier aplicación que utilice Formularios Windows Forms; si se omite, los componentes de Windows podrían no funcionar correctamente. Si el atributo no está presente, la aplicación utiliza el modelo de Apartamento multiproceso, que no se admite para Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] proyectos que utilizan el marco de trabajo de la aplicación no tienen que marcar el método **Main** con STAThread. El compilador de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] lo hace automáticamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el atributo <xref:System.STAThreadAttribute> al punto de entrada. Si el atributo <xref:System.MTAThreadAttribute?displayProperty=fullName> está presente, quítelo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si está desarrollando para el .NET Compact Framework, para el que el atributo <xref:System.STAThreadAttribute> no es necesario y no se admite.

## <a name="example"></a>Ejemplo
 En los siguientes ejemplos se muestra el uso correcto de <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]

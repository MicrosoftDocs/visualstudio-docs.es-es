---
title: 'CA2232: Puntos de entrada marcar Windows Forms con STAThread | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ef67681bcb0f16e8d7f75ebfcad079c85d47ab4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919291"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Marcar puntos de entrada de Windows Forms con STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] los proyectos que usan el marco de aplicación no es necesario que marcar el **Main** método con STAThread. El [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilador lo hace automáticamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el <xref:System.STAThreadAttribute> atributo al punto de entrada. Si el <xref:System.MTAThreadAttribute?displayProperty=fullName> atributo está presente, quítelo.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si está desarrollando para .NET Compact Framework, para que el <xref:System.STAThreadAttribute> atributo es necesario y no se admite.

## <a name="example"></a>Ejemplo
 Los ejemplos siguientes muestran el uso correcto de <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]




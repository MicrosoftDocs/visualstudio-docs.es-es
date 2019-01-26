---
title: Procedimiento Determinar mediante programación el actual elemento de Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e72928c6244ba15a96bdedd7aba6b59c1e50e708
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875100"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procedimiento Determinar mediante programación el actual elemento de Outlook
  Este ejemplo se usa el `Explorer.SelectionChange` eventos para mostrar el nombre de la carpeta actual y alguna información sobre el elemento seleccionado. El código, a continuación, muestra el elemento seleccionado.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Citas, contactos y elementos de correo electrónico en Microsoft Office Outlook.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)   
 [Cómo: Recuperar una carpeta por nombre mediante programación](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Cómo: Buscar un contacto específico mediante programación](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  

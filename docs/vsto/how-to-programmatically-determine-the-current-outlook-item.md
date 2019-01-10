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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7ed0a235a24b65b89a1b82ec47236f3f013f81dc
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/09/2019
ms.locfileid: "54153975"
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

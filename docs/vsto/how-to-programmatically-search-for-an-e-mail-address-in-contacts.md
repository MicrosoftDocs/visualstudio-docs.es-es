---
title: "Cómo: buscar una dirección de correo electrónico en los contactos mediante programación | Documentos de Microsoft"
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
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: d9ab451d433536c7ebf5931aa2c971b08ed5c09b
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-search-for-an-e-mail-address-in-contacts"></a>Cómo: Buscar una dirección de correo electrónico en los contactos mediante programación
  En este ejemplo se busca en una carpeta de contactos los contactos que tienen el nombre de dominio **ejemplo.com** en sus direcciones de correo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Para este ejemplo se necesita:  
  
-   Contactos que tengan el nombre de dominio **ejemplo.com** en sus direcciones de correo (por ejemplo, `somebody@example.com`) y que tengan nombres y apellidos.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con contactos](../vsto/working-with-contact-items.md)   
 [Cómo: enviar un correo electrónico mediante programación](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [Cómo: obtener acceso mediante programación a los contactos de Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Cómo: Agregar una entrada a los contactos de Outlook mediante programación](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  
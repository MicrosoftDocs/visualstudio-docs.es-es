---
title: Mediante la funcionalidad de Office dentro de Visual Studio | Documentos de Microsoft
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
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
ms.assetid: 593fd583-57e5-4ed5-8489-89f73b886c6c
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38eb32ac983d81d3ef94431d6275da643f632ae9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="using-office-functionality-inside-of-visual-studio"></a>Usar la funcionalidad de Office dentro de Visual Studio
  Cuando crea un proyecto de nivel de documento, el documento y la aplicación asociada se hospedan dentro de Visual Studio para que pueda diseñar y trabajar directamente con el documento. Si tiene una aplicación que se abra en Visual Studio de Microsoft Office, por lo general funciona según lo previsto. Sin embargo, algunas de las funcionalidades de la aplicación es diferente o no es accesible.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Protección de documentos  
 Microsoft Office Word y Microsoft Office Excel ofrecen documento características de protección que puede usar en los proyectos. Sin embargo, si está habilitada la protección de documentos mientras el documento está abierto en Visual Studio, puede impedir realizar algunos cambios de diseño. Para obtener más información, consulte [protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>Information Rights Management  
 Information Rights Management (IRM) está disponible en Microsoft Office Word y Microsoft Office Excel. IRM puede ayudarle a evitar que personas no autorizadas vean o modifiquen la información confidencial. Sin embargo, IRM también puede impedir que el código de ejecución. Para obtener más información, consulte [Information Rights Management y administra información general de extensiones de código](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Protección con contraseña  
 Documentos de Microsoft Office Word y libros de Microsoft Office Excel pueden establecerse para que no puedan abrirlos por alguien que no conoce la contraseña. Protección por contraseña trata de forma diferente en Word y Excel y puede afectar al proceso de desarrollo. Para obtener más información, consulte [protección con contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management y la información general de las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección con contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: Abrir soluciones de Office sin ejecutar código](../vsto/how-to-open-office-solutions-without-running-code.md)  
  
  
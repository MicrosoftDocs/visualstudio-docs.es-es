---
title: Use la funcionalidad de Office en Visual Studio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d1bcb827f068dd8c6577fed50e67d866ebba4886
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934627"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Use la funcionalidad de Office en Visual Studio
  Al crear un proyecto de nivel de documento, el documento y la aplicación asociada se hospedan dentro de Visual Studio para que pueda diseñar y trabajar directamente con el documento. Cuando haya una aplicación abierta en Visual Studio de Microsoft Office, por lo general funciona según lo previsto. Sin embargo, algunas de las funcionalidades de la aplicación es diferente o inaccesible.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="document-protection"></a>Protección de documentos  
 Microsoft Office Word y Microsoft Office Excel documento ofrecen las características de protección que puede usar en sus proyectos. Sin embargo, si está habilitada la protección de documentos mientras el documento está abierto en Visual Studio, puede impedir algunos cambios de diseño. Para obtener más información, consulte [protección en soluciones de nivel de documento de documentos](../vsto/document-protection-in-document-level-solutions.md).  
  
## <a name="information-rights-management"></a>De Information rights management  
 Information Rights Management (IRM) está disponible en Microsoft Office Word y Microsoft Office Excel. IRM puede ayudar a evitar que personas no autorizadas vean o modifiquen la información confidencial. Sin embargo, IRM también puede evitar que el código se ejecute. Para obtener más información, consulte [Information rights management y la introducción a las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md).  
  
## <a name="password-protection"></a>Protección con contraseña  
 Documentos de Microsoft Office Word y libros de Microsoft Office Excel se pueden establecer para que no se puede abrir por alguien que no conoce la contraseña. Protección con contraseña se controla de forma distinta en Word y Excel y puede afectar al proceso de desarrollo. Para obtener más información, consulte [protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md).  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management y la introducción a las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Cómo: Abrir soluciones de Office sin ejecutar código](../vsto/how-to-open-office-solutions-without-running-code.md)  

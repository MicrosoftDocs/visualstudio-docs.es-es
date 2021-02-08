---
title: Usar la funcionalidad de Office dentro de Visual Studio
description: Obtenga información sobre cómo el documento y la aplicación asociada de un proyecto de nivel de documento se hospedan en Visual Studio para que pueda trabajar directamente con el documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], document protection
- Office applications [Office development in Visual Studio]
- Office functionality inside Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 258ea4529a558c91eb115b82b35def4ca4ab6561
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838248"
---
# <a name="use-office-functionality-inside-of-visual-studio"></a>Usar la funcionalidad de Office dentro de Visual Studio
  Al crear un proyecto de nivel de documento, el documento y la aplicación asociada se hospedan en Visual Studio para que pueda diseñar y trabajar directamente con el documento. Si tiene una aplicación Microsoft Office abierta en Visual Studio, normalmente funciona según lo previsto. Sin embargo, parte de la funcionalidad de la aplicación es diferente o inaccesible.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="document-protection"></a>Protección de documentos
 Microsoft Office Word y Microsoft Office Excel ofrecen características de protección de documentos que puede usar en sus proyectos. Sin embargo, si está habilitada la protección de documentos mientras el documento está abierto en Visual Studio, puede impedir que realice algunos cambios de diseño. Para obtener más información, vea [protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md).

## <a name="information-rights-management"></a>Information Rights Management
 La información Rights Management (IRM) está disponible en Microsoft Office Word y Microsoft Office Excel. IRM puede ayudarle a evitar que personas no autorizadas vean o modifiquen información confidencial. Sin embargo, IRM también puede impedir que se ejecute el código. Para obtener más información, vea [información general sobre Information Rights Management y extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md).

## <a name="password-protection"></a>Protección con contraseña
 Microsoft Office documentos de Word y Microsoft Office libros de Excel se pueden establecer para que no se puedan abrir por alguien que no conozca la contraseña. La protección con contraseña se trata de forma diferente en Word y Excel, y puede afectar al proceso de desarrollo. Para obtener más información, consulte [protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md).

## <a name="see-also"></a>Vea también
- [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Información general sobre Information Rights Management y extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)
- [Cómo: abrir soluciones de Office sin ejecutar código](../vsto/how-to-open-office-solutions-without-running-code.md)

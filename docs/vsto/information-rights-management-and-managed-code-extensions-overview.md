---
title: Information Rights Management & extensiones de código administrado
description: Obtenga información acerca de Information Rights Management (IRM), una característica que puede ayudarle a evitar que personas no autorizadas vean o modifiquen información confidencial.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc300ac83674b8faf2bd4c0fc6128f60c28ee92b
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523054"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Información general sobre Information Rights Management y extensiones de código administrado
  Microsoft Office Word y Microsoft Office Excel proporcionan información Rights Management (IRM), una característica que puede ayudarle a evitar que personas no autorizadas vean o modifiquen información confidencial. Para obtener más información sobre cómo funciona la información Rights Management, vea la ayuda de en la aplicación de Office específica.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Ejecutar código subyacente a documentos con permisos restringidos
 Si la solución contiene un documento o un libro que usa IRM, de forma predeterminada, Word y Excel no permiten la ejecución de código. Si es el autor del documento o tiene acceso de control total, puede cambiar el valor predeterminado para que la solución funcione. Para obtener más información, vea [Cómo: permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM impide el uso de <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> para recuperar o manipular los datos almacenados en caché en el documento.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Usuarios finales para restringir los permisos a documentos que usan extensiones de código administrado
 Cualquier persona que tenga acceso de control total al documento o libro de la solución puede usar IRM para restringir los permisos. Por ejemplo, si un usuario final en el Departamento de contabilidad usa una solución que rellena automáticamente una hoja de cálculo con datos de una base de datos, es posible que el usuario quiera permitir el acceso de cambios solo a personas de su departamento y acceso de lectura a otros usuarios. Cuando el usuario agrega los permisos restringidos, de forma predeterminada, no se puede ejecutar el código subyacente de la hoja de cálculo y la hoja de cálculo no se rellenará con datos.

 Para solucionar el problema, alguien con acceso de control total al documento o libro debe cambiar la configuración de permisos predeterminada para permitir el acceso mediante programación al modelo de objetos. Para obtener más información, vea [Cómo: permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Consulte también
- [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)

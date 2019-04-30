---
title: Information rights management y la introducción a las extensiones de código administrado
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
ms.openlocfilehash: 109f6b85653a842f7c6fc9ce2d2c09b74113bbc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583925"
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Information rights management y la introducción a las extensiones de código administrado
  Microsoft Office Word y Microsoft Office Excel proporcionan Information Rights Management (IRM), una característica que puede ayudarle a evitar que personas no autorizadas vean o modifiquen la información confidencial. Para obtener más información acerca del funcionamiento de Information Rights Management, vea la Ayuda de la aplicación de Office específica.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="run-code-behind-documents-with-restricted-permissions"></a>Ejecute el código subyacente de los documentos con permisos restringidos
 Si la solución contiene un documento o libro que usa IRM, de forma predeterminada, Word y Excel no permiten que cualquier código que se ejecutará. Si es el autor del documento o tiene acceso de Control total, puede cambiar el valor predeterminado para que funcione la solución. Para obtener más información, vea [Cómo: Permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

 IRM impide el uso de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> para recuperar o manipular los datos que se almacena en caché en el documento.

## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Usuarios finales para restringir permisos a los documentos que utilizan extensiones de código administrado
 Cualquiera que tenga acceso de Control total en el documento o libro en la solución puede utilizar IRM para restringir los permisos. Por ejemplo, si un usuario final en el departamento de contabilidad utiliza una solución que rellena automáticamente una hoja de cálculo con datos de una base de datos, que el usuario desea permitir el acceso de lectura a otros usuarios y cambiar acceso solo a las personas de su departamento. Cuando el usuario agrega los permisos restringidos, de forma predeterminada, no se puede ejecutar el código subyacente de la hoja de cálculo y la hoja de cálculo no se rellenará con datos.

 Para corregir el problema, un usuario con acceso de Control total en el documento o libro debe cambiar la configuración de permisos predeterminada para permitir el acceso mediante programación al modelo de objetos. Para obtener más información, vea [Cómo: Permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).

## <a name="see-also"></a>Vea también
- [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)

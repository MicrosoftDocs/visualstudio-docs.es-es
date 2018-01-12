---
title: "Información general de las extensiones de código administrado y de Information Rights Management | Documentos de Microsoft"
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
- Information Rights Management [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- IRM [Office development in Visual Studio]
- documents [Office development in Visual Studio], restricted permissions
- rights management [Office development in Visual Studio]
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 561f17acd17cb34892d3f2d4f0eefa05dfced0e4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Información general sobre la administración de permisos sobre la información y las extensiones de código administrado
  Microsoft Office Word y Microsoft Office Excel proporcionan Information Rights Management (IRM), una característica que puede ayudarle a evitar que personas no autorizadas vean o modifiquen la información confidencial. Para obtener más información acerca del funcionamiento de Information Rights Management, vea la Ayuda de la aplicación de Office específica.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="running-code-behind-documents-with-restricted-permissions"></a>Ejecución de código subyacente de los documentos con permisos restringidos  
 Si la solución contiene un documento o libro que utilice IRM, de forma predeterminada, Word y Excel no permiten cualquier código que se ejecuta. Si el autor del documento o que tenga acceso de Control total, puede cambiar el valor predeterminado para que funcione la solución. Para obtener más información, consulte [Cómo: permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM impide el uso de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> para recuperar o manipular los datos que se almacena en caché en el documento.  
  
## <a name="end-users-restricting-permissions-to-documents-that-use-managed-code-extensions"></a>Usuarios finales restringen los permisos a los documentos que utilizan extensiones de código administrado  
 Cualquiera que tenga acceso de Control total en el documento o libro en la solución puede utilizar IRM para restringir los permisos. Por ejemplo, si un usuario final en el departamento de contabilidad utiliza una solución que rellena automáticamente una hoja de cálculo con datos de una base de datos, que el usuario desea permitir el acceso de lectura a otros usuarios y cambiar el acceso solo a las personas de su departamento. Cuando el usuario agrega los permisos restringidos, de forma predeterminada, no se puede ejecutar el código subyacente de la hoja de cálculo y la hoja de cálculo no se rellenará con datos.  
  
 Para corregir el problema, una persona con acceso de Control total en el documento o libro debe cambiar la configuración de permisos predeterminada para permitir el acceso mediante programación al modelo de objetos. Para obtener más información, consulte [Cómo: permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección con contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  
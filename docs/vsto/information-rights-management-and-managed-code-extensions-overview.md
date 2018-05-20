---
title: Información general de extensiones de código administrado y de Information rights management
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35a118774d50bcc697cd3ff5663fc26d8580ac88
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="information-rights-management-and-managed-code-extensions-overview"></a>Información general de extensiones de código administrado y de Information rights management
  Microsoft Office Word y Microsoft Office Excel proporcionan Information Rights Management (IRM), una característica que puede ayudarle a evitar que personas no autorizadas vean o modifiquen la información confidencial. Para obtener más información acerca del funcionamiento de Information Rights Management, vea la Ayuda de la aplicación de Office específica.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="run-code-behind-documents-with-restricted-permissions"></a>Ejecutar código subyacente de los documentos con permisos restringidos  
 Si la solución contiene un documento o libro que utilice IRM, de forma predeterminada, Word y Excel no permiten cualquier código que se ejecuta. Si el autor del documento o que tenga acceso de Control total, puede cambiar el valor predeterminado para que funcione la solución. Para obtener más información, consulte [Cómo: permitir que el código para que se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM impide el uso de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> para recuperar o manipular los datos que se almacena en caché en el documento.  
  
## <a name="end-users-to-restrict-permissions-to-documents-that-use-managed-code-extensions"></a>Usuarios finales para restringir los permisos a los documentos que utilizan extensiones de código administrado  
 Cualquiera que tenga acceso de Control total en el documento o libro en la solución puede utilizar IRM para restringir los permisos. Por ejemplo, si un usuario final en el departamento de contabilidad utiliza una solución que rellena automáticamente una hoja de cálculo con datos de una base de datos, que el usuario desea permitir el acceso de lectura a otros usuarios y cambiar el acceso solo a las personas de su departamento. Cuando el usuario agrega los permisos restringidos, de forma predeterminada, no se puede ejecutar el código subyacente de la hoja de cálculo y la hoja de cálculo no se rellenará con datos.  
  
 Para corregir el problema, una persona con acceso de Control total en el documento o libro debe cambiar la configuración de permisos predeterminada para permitir el acceso mediante programación al modelo de objetos. Para obtener más información, consulte [Cómo: permitir que el código para que se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección con contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Proteger soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  
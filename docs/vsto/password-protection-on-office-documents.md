---
title: "Protección con contraseña en documentos de Office | Documentos de Microsoft"
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
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
ms.assetid: 9cee99c8-73c6-4f89-9d5e-7912c876ff96
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: f24c0493a66651a5d95925fd6777ba3e1cdd1658
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="password-protection-on-office-documents"></a>Protección mediante contraseña en documentos de Office
  Es posible establecer una contraseña en los documentos de Microsoft Office Word y libros de Microsoft Office Excel para que no puedan abrirlos por alguien que no conoce la contraseña. Esta opción se denomina **contraseña al abrir**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede crear proyectos de nivel de documento usando los documentos existentes y los libros que tienen **contraseña al abrir** habilitado. El comportamiento en Visual Studio es diferente para los documentos de Word y Excel que tienen **contraseña al abrir** habilitado.  
  
 Para obtener información acerca de cómo habilitar **contraseña al abrir**, consulte la Ayuda de Word o Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Comportamiento de Excel y Word  
 Cada vez que abre un libro de Excel en Visual Studio que tenga **contraseña al abrir** habilitado, Excel le pide la contraseña. Cuando se compila una solución le se pedirá la contraseña de nuevo, porque el documento se abre durante la compilación.  
  
 La primera vez que abra un documento de Word en Visual Studio que tenga **contraseña al abrir** habilitado, Word le pide la contraseña. Después de escribir correctamente la contraseña, **contraseña al abrir** se quitan del documento y abrir el documento ya no necesitará una contraseña. Si desea que el documento de la solución que requieran una contraseña antes de que se puede abrir, debe habilitar **contraseña al abrir** después de la compilación final y antes de implementar la solución.  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Information Rights Management y la información general de las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Cómo: permitir que el código ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseño y creación de soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  
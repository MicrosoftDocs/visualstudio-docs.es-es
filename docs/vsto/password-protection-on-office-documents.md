---
title: Protección con contraseña en documentos de Office | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a278677b40f8da703c7f3287851c2f82fb95a21c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572717"
---
# <a name="password-protection-on-office-documents"></a>Protección con contraseña en documentos de Office
  Es posible establecer una contraseña en los documentos de Microsoft Office Word y libros de Microsoft Office Excel para que no puedan abrirlos por alguien que no conoce la contraseña. Esta opción se denomina **contraseña al abrir**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede crear proyectos de nivel de documento usando los documentos existentes y los libros que tienen **contraseña al abrir** habilitado. El comportamiento en Visual Studio es diferente para los documentos de Word y Excel que tienen **contraseña al abrir** habilitado.  
  
 Para obtener información acerca de cómo habilitar **contraseña al abrir**, consulte la Ayuda de Word o Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Comportamiento de Excel y Word  
 Cada vez que abre un libro de Excel en Visual Studio que tenga **contraseña al abrir** habilitado, Excel le pide la contraseña. Cuando se compila una solución le se pedirá la contraseña de nuevo, porque el documento se abre durante la compilación.  
  
 La primera vez que abra un documento de Word en Visual Studio que tenga **contraseña al abrir** habilitado, Word le pide la contraseña. Después de escribir correctamente la contraseña, **contraseña al abrir** se quitan del documento y abrir el documento ya no necesitará una contraseña. Si desea que el documento de la solución que requieran una contraseña antes de que se puede abrir, debe habilitar **contraseña al abrir** después de la compilación final y antes de implementar la solución.  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Información general de extensiones de código administrado y de Information rights management](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Cómo: permitir que el código para que se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  
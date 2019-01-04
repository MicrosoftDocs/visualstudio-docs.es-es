---
title: Protección mediante contraseña en documentos de Office
ms.date: 02/02/2017
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
ms.openlocfilehash: 4603a6f5722279ccdaf057d30d3bc6e911c4c47e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857006"
---
# <a name="password-protection-on-office-documents"></a>Protección mediante contraseña en documentos de Office
  Es posible establecer una contraseña en los documentos de Microsoft Office Word y libros de Microsoft Office Excel para que no se puede abrir por alguien que no conoce la contraseña. Esta opción se denomina **contraseña al abrir**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Puede crear proyectos de nivel de documento con los documentos existentes y los libros que tienen **contraseña al abrir** habilitado. El comportamiento en Visual Studio es diferente para los documentos de Word y Excel que tienen **contraseña al abrir** habilitado.  
  
 Para obtener información acerca de cómo habilitar **contraseña al abrir**, consulte la Ayuda de Word o Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Comportamiento de Excel y Word  
 Cada vez que abre un libro de Excel en Visual Studio que tiene **contraseña al abrir** habilitado, Excel le pedirá la contraseña. Cuando compile la solución solicitará la contraseña de nuevo, ya que se abre el documento durante la compilación.  
  
 La primera vez abra un documento de Word en Visual Studio que tiene **contraseña al abrir** habilitado, Word le pedirá la contraseña. Después de escribir correctamente la contraseña, **contraseña al abrir** se quitan del documento y abrir el documento ya no requiere una contraseña. Si desea que el documento de la solución que requieran una contraseña antes de que se puede abrir, debe habilitar **contraseña al abrir** después de la compilación final y antes de implementar la solución.  
  
## <a name="see-also"></a>Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Information rights management y la introducción a las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Cómo: Permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  

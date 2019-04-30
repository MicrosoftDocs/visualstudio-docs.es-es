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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e3c9521389ce348a482f35ec95c9766edea49f5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977905"
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
- [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)
- [Information rights management y la introducción a las extensiones de código administrado](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Cómo: Permitir que el código se ejecute detrás de documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)

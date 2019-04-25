---
title: Procedimiento Abrir soluciones de Office sin ejecutar código
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], opening
- opening Office solutions
- bypassing assemblies
- solutions [Office development in Visual Studio], opening
- assemblies [Office development in Visual Studio], bypassing
- Office documents [Office development in Visual Studio, opening without running code
- documents [Office development in Visual Studio], opening without running code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9b9a88aff9cd587f695ace56c44eaf9c8fcb8875
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117205"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Procedimiento Abrir soluciones de Office sin ejecutar código
  Una solución de Microsoft Office creada con las extensiones de código administrado se ejecuta incluso si la configuración de seguridad en la aplicación de Office del usuario final está establecida en High. Esto es porque la seguridad del código de ensamblado de .NET es administrado por Microsoft .NET Framework, no por Microsoft Office.

 Sin embargo, hay veces cuando desea abrir un documento sin ejecutar el código. Por ejemplo, el código que se ejecuta cuando se abre el documento podría alterar el contenido, pero desea actualizar el aspecto del documento antes de los cambios de código. O desea enviar el documento con cierta información en ella a otra persona, y no desea que el código para ejecutar y posiblemente modificar su contenido.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Hay varias maneras de abrir un documento o libro que contiene las extensiones de código administrado sin ejecutar el código de ensamblado.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Para omitir el ensamblado mediante el uso de la tecla MAYÚS

- Abrir documentos y libros desde el **archivo** menú mientras mantiene presionada la **MAYÚS** clave para impedir que generar eventos de inicialización mientras se abre el documento de Word y Excel.

    > [!NOTE]
    >  Si abre un documento o libro desde el **Introducción** panel de tareas, manteniendo presionada la tecla **MAYÚS** no se omite el código. Además, manteniendo presionada la tecla MAYÚS no impide que los eventos que se produce después de que el documento está abierto.

     Este método es útil si desea abrir un documento para realizar cambios sin ejecutar el código y modificar primero el documento.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Para omitir un ensamblado cambiando el nombre o eliminarlo

- Si tiene los permisos necesarios en el equipo donde se encuentra el ensamblado, puede cambiar el nombre o quite el ensamblado para que el documento o libro no puede encontrarlo. Esto da como resultado un error cada vez que se abre el documento de Office.

     Si la solución está usando varias personas, este método impide que la solución se ejecute para todas ellas. Esto puede ser útil si se encuentra un problema en el código o un servidor que se hace referencia y desea evitar que los usuarios de su ejecución.

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifiestos de aplicación e implementación de soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)

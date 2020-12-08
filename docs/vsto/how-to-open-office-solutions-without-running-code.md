---
title: 'Cómo: abrir soluciones de Office sin ejecutar código'
description: Obtenga información sobre cómo puede abrir un documento o un libro que contenga extensiones de código administrado sin ejecutar el código de ensamblado.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8339f21fbf7add4335941360b73d42700ef6e635
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844925"
---
# <a name="how-to-open-office-solutions-without-running-code"></a>Cómo: abrir soluciones de Office sin ejecutar código
  Una solución Microsoft Office creada con extensiones de código administrado se ejecuta incluso si la configuración de seguridad de la aplicación de Office del usuario final está establecida en alta. Esto se debe a que la seguridad del código de ensamblado .NET se administra mediante el marco de Microsoft .NET, no Microsoft Office.

 Sin embargo, hay ocasiones en las que puede que desee abrir un documento sin ejecutar el código. Por ejemplo, el código que se ejecuta cuando se abre el documento puede alterar el contenido, pero desea actualizar la apariencia del documento antes de que el código lo cambie. O bien, puede que desee enviar el documento con cierta información a alguien, y no desea que el código se ejecute y, posiblemente, modifique el contenido.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Hay varias maneras de abrir un documento o un libro que contiene extensiones de código administrado sin ejecutar el código del ensamblado.

## <a name="to-bypass-the-assembly-by-using-the-shift-key"></a>Para omitir el ensamblado mediante la tecla Mayús

- Abra documentos y libros desde el menú **archivo** manteniendo presionada la tecla **MAYÚS** para evitar que Word y Excel generen eventos de inicialización mientras se está abriendo el documento.

    > [!NOTE]
    > Si abre un documento o un libro desde el panel de tareas **Introducción** , mantener presionada la **tecla Mayús** no omite el código. Además, mantener presionada la tecla Mayús no impide que se generen eventos después de abrir el documento.

     Este método es útil si desea abrir un documento para realizar cambios sin el código en ejecución y modificar el documento primero.

## <a name="to-bypass-an-assembly-by-renaming-or-removing-it"></a>Para omitir un ensamblado mediante el cambio de nombre o su eliminación

- Si tiene los permisos necesarios en el equipo donde se encuentra el ensamblado, puede cambiar el nombre o quitar el ensamblado para que el documento o el libro no lo encuentre. Esto provoca que se produzca un error cada vez que se abre el documento de Office.

     Si varias personas usan la solución, este método impide que la solución se ejecute para todos ellos. Esto puede ser útil si se encuentra un problema en el código o en un servidor al que se hace referencia y desea detener la ejecución de todos los usuarios.

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)

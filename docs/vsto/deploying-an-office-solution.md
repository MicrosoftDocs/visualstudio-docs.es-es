---
title: Implementar una solución de Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office applications [Office development in Visual Studio], deploying Office solutions
- Office development in Visual Studio, deploying Office solutions
- ClickOnce deployment [Office development in Visual Studio], troubleshooting
- deploying applications [Office development in Visual Studio], Office solutions (2007 system)
- Office development in Visual Studio, troubleshooting
- Office development in Visual Studio, event viewer
- ClickOnce deployment [Office development in Visual Studio], about ClickOnce solution deployments
- Office solutions [Office development in Visual Studio], deploying
- deploying applications [Office development in Visual Studio], troubleshooting
- solutions [Office development in Visual Studio], deploying Office solutions (2007 system)
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abe4951c8ef748231e8c2f0167253caf49fbf1eb
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551594"
---
# <a name="deploy-an-office-solution"></a>Implementar una solución de Office
  Puede implementar soluciones de Office mediante ClickOnce o Windows Installer. Si usa ClickOnce, se reducirá el número de pasos que requiere la implementación y actualización de la solución. Si utiliza Windows Installer, obtendrá control sobre cómo se instala la solución y qué páginas muestra el programa de instalación cuando los usuarios instalan la solución.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="deploy-a-solution-by-using-clickonce"></a>Implementar una solución mediante ClickOnce
 Al implementar una solución mediante ClickOnce, esta se publica en una ubicación centralizada donde los usuarios pueden instalarla y ejecutarla. Puede actualizar la solución sin tener que distribuir un nuevo programa de instalación a los usuarios.  Esta opción de implementación es más sencilla, pero no puede mostrar a los usuarios las páginas de instalación personalizadas. Además, las soluciones se deben instalar varias veces en cualquier equipo que tenga más de un usuario. Consulte [implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

## <a name="deploy-a-solution-by-using-windows-installer"></a>Implementar una solución mediante Windows Installer
 Al implementar una solución mediante Windows Installer, distribuirá un programa de instalación a los usuarios y los usuarios instalarán la solución mediante ese programa. El programa de instalación puede instalar una solución para todos los usuarios de un equipo a la vez, en lugar de solo para el usuario actual. También tendrá un poco más de control sobre las opciones que se muestran a los usuarios cuando instalan la solución. Por ejemplo, puede mostrar un contrato de licencia o permitir que los usuarios instalen componentes específicos de una solución. Sin embargo, si actualiza la solución, debe distribuir un nuevo programa de instalación. Consulte [implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="see-also"></a>Vea también
- [Proteger soluciones de Office](../vsto/securing-office-solutions.md)
- [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Implementar una solución de Office mediante Windows Installer](../vsto/deploying-an-office-solution-by-using-windows-installer.md)
- [Solucionar problemas de implementación de soluciones de Office](../vsto/troubleshooting-office-solution-deployment.md)

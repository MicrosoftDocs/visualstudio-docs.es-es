---
title: Extender el empaquetado de SharePoint e implementación | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb98e2b1c83ff06570a77dc84ce6a7bf690f81d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097003"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Ampliar la implementación y empaquetado de SharePoint
  El proceso de empaquetado e implementación de proyectos de SharePoint se puede ampliar.

## <a name="create-deployment-steps"></a>Crear pasos de implementación
 Al implementar un proyecto de SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] ejecuta una serie de pasos de implementación. Visual Studio incluye pasos de implementación integrados para muchas tareas, como retirar y agregar soluciones. Sin embargo, también puede crear sus propios pasos de implementación.

 Para ver un tutorial que muestra cómo crear un paso de implementación, consulte [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Crear configuraciones de implementación
 Una configuración de implementación es un conjunto de pasos de implementación que se ejecuta en relación con un proyecto determinado, pero que puede afectar a todos los elementos del proyecto de SharePoint. Cada configuración de implementación incluye un conjunto de pasos que se ejecuta cuando el proyecto se implementa y otro conjunto que se ejecuta cuando ese proyecto se retira. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] incluye dos configuraciones de implementación integradas, pero también puede crear sus propios. Cuando crea una configuración de implementación, puede incluir tanto pasos de implementación integrados como pasos de implementación de su propia cosecha.

 Para ver un tutorial que muestra cómo crear una configuración de implementación, consulte [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Ejecute código al implementar o retirar una solución de SharePoint
 Puede controlar eventos para realizar más tareas al implementar o retirar una solución de SharePoint. Visual Studio genera eventos que puede controlar en los siguientes escenarios:

- Antes y después de que cada paso de implementación se ejecute para un elemento del proyecto de SharePoint. Para obtener más información, vea [Cómo: Ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Antes y después de que un proyecto de SharePoint se implemente o retire Para obtener más información, vea [Cómo: Ejecutar código cuando un proyecto de SharePoint se está implementando o retirando](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Controlar conflictos de implementación
 Algunos tipos de elementos de proyecto de SharePoint, como los módulos, los elementos web, las instancias de lista y los tipos de contenido, proporcionan una resolución integrada de conflictos de implementación. Al implementar una solución que contiene uno de estos elementos de proyecto, Visual Studio comprueba primero si ya existe un archivo en el sitio de SharePoint con el mismo nombre, dirección URL o identificador que un archivo en el elemento que se va a implementar. Si existe un conflicto, Visual Studio puede resolver el conflicto automáticamente, o bien pedirle que decida si quiere que Visual Studio resuelva el conflicto o cancele la implementación. Para obtener más información, consulta [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Puede extender esta característica suministrando un código propio que busca y resuelve conflictos de implementación. Para obtener más información, vea [Cómo: Controlar conflictos de implementación](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Ejecutar operaciones de línea de comandos antes o después de implementar un proyecto
 Si quiere ejecutar una operación de línea de comandos cuando hay implementada una solución de SharePoint, puede establecer las propiedades <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio ejecuta estos comandos antes y después de que el proyecto se implemente.

 En algunos casos, pueden producirse conflictos de implementación. Hay varias formas de resolver estos conflictos. Para obtener más información, consulte [SharePoint solucionar problemas de empaquetado e implementación](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Personalizar las reglas de validación
 Antes de implementar un paquete de solución (.wsp), puede crear reglas personalizadas de validación de características y paquetes para comprobar la validez de la característica o el paquete. Así, por ejemplo, puede mostrar información, advertencias o errores a los desarrolladores para ayudarles a solucionar problemas de validación. Para obtener más información, vea [Cómo: Creación de reglas de validación para las soluciones de SharePoint de características y paquetes](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Vea también
- [Cómo: Ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Cómo: Crear paquetes y características personalizado reglas de validación para las soluciones de SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)

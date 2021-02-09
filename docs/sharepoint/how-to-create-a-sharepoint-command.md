---
title: 'Cómo: crear un comando de SharePoint | Microsoft Docs'
description: Aprenda a crear un comando de SharePoint personalizado para llamar a la API del modelo de objetos de servidor en una extensión de herramientas de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 51b80124f7cf550843ad346e9d1e1c0b21ccd0f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923353"
---
# <a name="how-to-create-a-sharepoint-command"></a>Cómo: crear un comando de SharePoint
  Si desea usar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear un *comando de SharePoint* personalizado para llamar a la API. El comando de SharePoint se define en un ensamblado que puede llamar directamente al modelo de objetos de servidor.

 Para obtener más información sobre el propósito de los comandos de SharePoint, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Para crear un comando de SharePoint

1. Cree un proyecto de biblioteca de clases que tenga la siguiente configuración:

    - Tiene como destino el .NET Framework 3,5. Para obtener más información sobre cómo seleccionar la plataforma de destino, vea [Cómo: establecer como destino una versión de la .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Tiene como destino la plataforma AnyCPU o x64. De forma predeterminada, la plataforma de destino para los proyectos de biblioteca de clases es AnyCPU. Para obtener más información sobre cómo seleccionar la plataforma de destino, consulte [Cómo: configurar proyectos para plataformas de destino](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > No se puede implementar un comando de SharePoint en el mismo proyecto que define una extensión de herramientas de SharePoint, ya que los comandos de SharePoint se destinan al .NET Framework 3,5 y las extensiones de herramientas de SharePoint tienen como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Debe definir los comandos de SharePoint que usa la extensión en un proyecto independiente. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint.Commands

    - Microsoft.SharePoint

3. En una clase del proyecto, cree un método que defina el comando de SharePoint. El método debe cumplir las siguientes directrices:

    - Puede tener uno o dos parámetros.

         El primer parámetro debe ser un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> objeto. Este objeto proporciona Microsoft. SharePoint. SPSite o Microsoft. SharePoint. SPWeb en el que se ejecuta el comando. También proporciona un <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> objeto que se puede usar para escribir mensajes en la ventana de **salida** o en **lista de errores** ventana de Visual Studio.

         El segundo parámetro puede ser un tipo de su elección, pero este parámetro es opcional. Puede Agregar este parámetro al comando de SharePoint si necesita pasar datos de la extensión de herramientas de SharePoint al comando.

    - Puede tener un valor devuelto, pero esto es opcional.

    - El segundo parámetro y el valor devuelto deben ser un tipo que se pueda serializar mediante el Windows Communication Foundation (WCF). Para obtener más información, vea [tipos admitidos por el serializador de contrato de datos](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) y [usar la clase XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - El método puede tener cualquier visibilidad (**pública**, **interna** o **privada**) y puede ser estática o no estática.

4. Aplique <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> al método. Este atributo especifica un identificador único para el comando; Este identificador no tiene que coincidir con el nombre del método.

     Debe especificar el mismo identificador único al llamar al comando desde la extensión de herramientas de SharePoint. Para obtener más información, vea [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra un comando de SharePoint con el identificador `Contoso.Commands.UpgradeSolution` . Este comando usa las API del modelo de objetos de servidor para actualizar a una solución implementada.

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 Además del primer <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro implícito, este comando también tiene un parámetro de cadena personalizado que contiene la ruta de acceso completa del archivo. wsp que se está actualizando al sitio de SharePoint. Para ver este código en el contexto de un ejemplo más grande, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Compilación del código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint.Commands

- Microsoft.SharePoint

## <a name="deploying-the-command"></a>Implementar el comando
 Para implementar el comando, incluya el ensamblado de comandos en el mismo [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (*VSIX*) con el ensamblado de extensión que usa el comando. También debe agregar una entrada para el ensamblado de comandos en el archivo Extension. vsixmanifest. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Cómo: ejecutar un comando de SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

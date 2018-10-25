---
title: 'Cómo: personalizar un paquete de solución de SharePoint mediante destinos de MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 434d673c62d0b26efa1559db7d7d98747146fd2d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889695"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Cómo: personalizar un paquete de solución de SharePoint mediante destinos de MSBuild
  Mediante el uso de destinos de MSBuild en un símbolo del sistema, puede personalizar cómo Visual Studio crea los archivos de paquete de SharePoint (*.wsp*). Por ejemplo, puede personalizar las propiedades de MSBuild para cambiar el directorio intermedio del paquete y los grupos de elementos de MSBuild que especifican los archivos enumerados.  
  
## <a name="customize-and-run-msbuild-targets"></a>Personalizar y ejecutar destinos de MSBuild  
 Si personaliza los destinos BeforeLayout y AfterLayout, puede realizar las tareas antes de diseño del paquete, como agregar, quitar o modificar los archivos que se empaquetan.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Para personalizar el destino BeforeLayout  
  
1. Abra un editor, como el Bloc de notas y, a continuación, agregue el código siguiente.  
  
   ```xml  
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
     <Target Name="BeforeLayout">  
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
     </Target>  
   </Project>  
   ```  
  
    En este ejemplo se muestra un mensaje antes del empaquetado de este destino.  
  
2. Nombre del archivo **CustomLayout.SharePoint.targets**y, a continuación, guárdelo en la carpeta del proyecto de SharePoint.  
  
3. Abra el proyecto, abra el menú contextual y, a continuación, elija **descargar el proyecto**.  
  
4. En **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **editar**  *\<NombreDelProyecto > .vbproj* o **editar**  *\<NombreDelProyecto > .csproj*.  
  
5. Después de la `Import` línea cerca del final del archivo del proyecto, agregue la siguiente línea.  
  
   ```xml  
   <Import Project="CustomLayout.SharePoint.targets" />  
   ```  
  
6. Guarde el archivo de proyecto y ciérrelo.  
  
7. En **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **recargar el proyecto**.  
  
   Al publicar el proyecto, aparecerá el mensaje en la salida antes de que comience el empaquetado.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Para personalizar el destino AfterLayout  
  
1. En la barra de menús, elija **archivo** > **abierto** > **archivo**.  
  
2. En el **abrir archivo** cuadro de diálogo, vaya a la carpeta del proyecto, elija el archivo CustomLayout.target y, a continuación, elija el **abierto** botón.  
  
3. Justo antes del `</Project>` etiqueta, agregue el código siguiente:  
  
   ```xml  
   <Target Name="AfterLayout">  
     <Message Importance="high" Text="In the AfterLayout Target"></Message>  
   </Target>  
   ```  
  
    Este ejemplo muestra un mensaje después de que se empaqueta este destino.  
  
4. Guarde y cierre el archivo de destinos.  
  
5. Reinicie Visual Studio y, a continuación, abra el proyecto.  
  
   Al publicar el proyecto, aparece el mensaje BeforeLayout antes de empaquetado y, aparece el mensaje de AfterLayout cuando finalice el empaquetado.  
  
## <a name="see-also"></a>Vea también
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  

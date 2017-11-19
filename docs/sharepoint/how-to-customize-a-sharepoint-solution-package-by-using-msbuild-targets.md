---
title: "Cómo: personalizar un paquete de solución de SharePoint mediante el uso de destinos de MSBuild | Documentos de Microsoft"
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
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 758cf3e62621c22f3f97dc62b70c745afb860b8a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Cómo: Personalizar un paquete de solución de SharePoint con los destinos de MSBuild
  Mediante el uso de destinos de MSBuild en un símbolo del sistema, puede personalizar el modo en que Visual Studio crea los archivos de paquete de SharePoint (.wsp). Por ejemplo, puede personalizar las propiedades de MSBuild para cambiar el directorio intermedio del paquete y los grupos de elementos de MSBuild que especifican los archivos enumerados.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Personalizar y ejecutar destinos de MSBuild  
 Si personaliza el destino BeforeLayout y AfterLayout, puede realizar las tareas antes de diseño del paquete, como agregar, quitar o modificar los archivos que se empaquetarán.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Para personalizar el destino BeforeLayout  
  
1.  Abra un editor, como el Bloc de notas y, a continuación, agregue el código siguiente.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     En este ejemplo se muestra un mensaje antes del empaquetado de este destino.  
  
2.  Asignar nombre al archivo **CustomLayout.SharePoint.targets**y, a continuación, guárdelo en la carpeta para el proyecto de SharePoint.  
  
3.  Abra el proyecto, abra el menú contextual y, a continuación, elija **descargar el proyecto**.  
  
4.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **editar***ProjectName***.vbproj** o **Editar***ProjectName***.csproj**.  
  
5.  Después de la `Import` línea cerca del final del archivo del proyecto, agregue la siguiente línea.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Guarde el archivo de proyecto y ciérrelo.  
  
7.  En **el Explorador de soluciones**, abra el menú contextual para el proyecto y, a continuación, elija **recargar el proyecto**.  
  
 Al publicar el proyecto, el mensaje aparecerá en la salida antes de que comience el empaquetado.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Para personalizar el destino AfterLayout  
  
1.  En la barra de menús, elija **archivo**, **abiertos**, **archivo**.  
  
2.  En el **archivos abiertos** cuadro de diálogo, desplácese hasta la carpeta del proyecto, elija el archivo CustomLayout.target y, a continuación, elija la **abiertos** botón.  
  
3.  Justo antes del `</Project>` etiqueta, agregue el código siguiente:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     En este ejemplo se muestra un mensaje después de que se empaqueta este destino.  
  
4.  Guarde y cierre el archivo de destino.  
  
5.  Reinicie Visual Studio y, a continuación, abra el proyecto.  
  
 Al publicar el proyecto, aparece el mensaje de BeforeLayout antes del comienzo de empaquetado, y aparece el mensaje AfterLayout cuando finaliza de empaquetado.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
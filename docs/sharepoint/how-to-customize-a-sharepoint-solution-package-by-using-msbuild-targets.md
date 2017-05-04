---
title: "C&#243;mo: Personalizar un paquete de soluci&#243;n de SharePoint con los destinos de MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "desarrollo de SharePoint en Visual Studio, paquetes"
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Personalizar un paquete de soluci&#243;n de SharePoint con los destinos de MSBuild
  Utilizando los destinos de MSBuild en el símbolo del sistema, puede personalizar la forma en que Visual Studio crea los archivos de paquete de SharePoint \(.wsp\).  Por ejemplo, puede personalizar las propiedades de MSBuild para cambiar el directorio intermedio del paquete y los grupos de elementos de MSBuild que especifican los archivos enumerados.  
  
## Personalizar y ejecutar destinos de MSBuild  
 Si personaliza los destinos de BeforeLayout y AfterLayout, puede realizar tareas antes de diseño del paquete, como agregar, quitar, o archivos de modificación que se empaquetan.  
  
#### Para personalizar el destino BeforeLayout  
  
1.  Abra un editor, como el Bloc de notas, y después agregue el código siguiente.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Este ejemplo muestra un mensaje antes de paquete de este destino.  
  
2.  Asigne al archivo **CustomLayout.SharePoint.targets**, y guárdelo en la carpeta del proyecto de SharePoint.  
  
3.  Abra el proyecto, abra el menú contextual y, a continuación **Descargar el proyecto**.  
  
4.  En **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación **edición***ProjectName***.vbproj** o **edición***ProjectName***.csproj**.  
  
5.  Después de la línea de `Import` cerca del final del archivo de proyecto, agregue la línea siguiente.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Guarde el archivo de proyecto y ciérrelo.  
  
7.  En **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación **volver a cargar el proyecto**.  
  
 Al publicar el proyecto, el mensaje aparecerá en la salida antes de que comience el empaquetado.  
  
#### Para personalizar el destino AfterLayout  
  
1.  En la barra de menú, elija **archivo**, **Abierta**, **archivo**.  
  
2.  En el cuadro de diálogo de **Abrir archivo** , navegue a la carpeta del proyecto, elija el archivo de CustomLayout.target, y elija el botón de **Abierta** .  
  
3.  Justo antes de la etiqueta de `</Project>` , agregue el código siguiente:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Este ejemplo muestra un mensaje después de que se empaquete este destino.  
  
4.  Guarde y cierre el archivo de destinos.  
  
5.  Reinicie Visual Studio, y vuelva a abrir el proyecto.  
  
 Al publicar el proyecto, el mensaje de BeforeLayout aparece antes que empaquete inicio, y el mensaje AfterLayout aparece cuando empaquete finalice.  
  
## Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
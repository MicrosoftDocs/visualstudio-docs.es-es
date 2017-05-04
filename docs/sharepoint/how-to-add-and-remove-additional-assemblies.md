---
title: "C&#243;mo: Agregar y quitar ensamblados adicionales | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.RAD.CustomAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Desarrollo de SharePoint en Visual Studio, paquetes"
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Agregar y quitar ensamblados adicionales
  Si un paquete de SharePoint depende de otros ensamblados para la funcionalidad o los datos, puede agregar esos ensamblados al paquete de solución \(.wsp\).  De esta manera, el servidor de SharePoint se asegura de que los ensamblados personalizados se instalan con un paquete.  
  
 También puede agregar y cambiar los controles seguros y los archivos de recursos de clase asociados a los ensamblados.  
  
## Agregar ensamblados, controles seguros y recursos de clase adicionales  
 Puede agregar ensamblados adicionales al paquete de solución de SharePoint.  Los ensamblados adicionales de una solución en espacio aislado se implementan en la memoria caché global de ensamblados, pero los elementos de proyecto de SharePoint incluidos en una solución en espacio aislado se agregan a la base de datos de contenido.  También puede agregar controles seguros y recursos de clase a estos ensamblados adicionales.  Para obtener más información sobre los controles seguros, vea [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o “Creación de una entrada SafeControl” en [Implementación de elementos web en SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### Para agregar un ensamblado existente  
  
1.  Abra el **Diseñador de paquetes**.  Para obtener más información, vea [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la pestaña **Opciones avanzadas**.  
  
3.  Elija el botón **Agregar** y después elija **Agregar ensamblado existente** de la lista.  
  
     Aparecerá el cuadro de diálogo **Agregar ensamblado existente**.  
  
4.  Elija los puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile")\) y después elija el ensamblado que desee agregar.  Por motivos de portabilidad, se recomienda utilizar una ruta de acceso relativa al ensamblado seleccionado.  
  
5.  Para el **Destino de la implementación**, elija el botón de opción **GlobalAssemblyCache** para implementar el ensamblado en la caché global de ensamblados o elija el botón de opción **WebApplication** para implementar el ensamblado en la carpeta WebApplication del servidor que ejecuta SharePoint.  
  
#### Para agregar un ensamblado desde la salida del proyecto  
  
1.  Abra el **Diseñador de paquetes**.  
  
     Para obtener más información, vea [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la pestaña **Opciones avanzadas**.  
  
3.  Elija el botón **Agregar** y después elija **Agregar ensamblado desde la salida del proyecto** de la lista.  
  
     Aparecerá el cuadro de diálogo **Agregar ensamblado desde la salida del proyecto**.  
  
4.  En la lista **Proyecto de origen**, elija el proyecto de origen que desea agregar.  
  
5.  Para el **Destino de la implementación**, elija el botón de opción **GlobalAssemblyCache** para implementar el ensamblado en la caché global de ensamblados o elija el botón de opción **WebApplication** para implementar el ensamblado en la carpeta WebApplication del servidor que ejecuta SharePoint.  
  
#### Para agregar un control seguro  
  
1.  Abra el cuadro de diálogo **Editar ensamblado existente**.  Para ello, abra el Diseñador de paquetes, elija la pestaña **Opciones avanzadas**, elija un ensamblado y, a continuación, elija el botón **Editar**.  
  
2.  En el panel **Controles seguros**, elija el botón **Haga clic aquí para agregar un nuevo elemento**.  
  
3.  En la columna **Nombre del ensamblado**, escriba el nombre del ensamblado.  
  
4.  En la columna **Espacio de nombres**, escriba el nombre del espacio de nombres para el control seguro.  
  
5.  En la columna **Nombre de tipo**, escriba el nombre del tipo.  
  
#### Para agregar un recurso de clase  
  
1.  Abra el cuadro de diálogo **Editar ensamblado existente**.  Para ello, abra el Diseñador de paquetes, elija la pestaña **Opciones avanzadas**, elija un ensamblado y, a continuación, elija el botón **Editar**.  
  
2.  En el panel **Recursos de clase**, elija el botón **Haga clic aquí para agregar un nuevo elemento**.  
  
3.  En la columna **Nombre de archivo**, elija los puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](../sharepoint/media/mwellipsis.png "Elipse del Diseñador de ASP.NET Mobile")\) y elija el recurso de clase que desee agregar.  
  
## Eliminar ensamblados personalizados  
 Puede eliminar los ensamblados de un paquete de SharePoint o eliminar los controles seguros y los recursos de clase de los ensamblados existentes.  
  
#### Para eliminar un ensamblado existente  
  
1.  Abra el **Diseñador de paquetes**.  Para obtener más información, vea [Cómo: Personalizar un paquete de solución de SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Elija la pestaña **Opciones avanzadas**.  
  
3.  En el panel **Ensamblados adicionales**, elija el ensamblado que desee eliminar.  
  
4.  Elija el botón **Eliminar**.  
  
#### Para eliminar un control seguro de un ensamblado  
  
1.  Abra el cuadro de diálogo **Editar ensamblado existente**.  Para ello, abra el Diseñador de paquetes, elija la pestaña **Opciones avanzadas**, elija un ensamblado y, a continuación, elija el botón **Editar**.  
  
2.  Elija el control seguro que desee eliminar.  
  
3.  Elija la tecla Supr.  
  
#### Para eliminar un recurso de clase de un ensamblado  
  
1.  Abra el cuadro de diálogo **Editar ensamblado existente**.  Para ello, abra el Diseñador de paquetes, elija la pestaña **Opciones avanzadas**, elija un ensamblado y, a continuación, elija el botón **Editar**.  
  
2.  Elija el recurso de clase que desee eliminar.  
  
3.  Elija la tecla Supr.  
  
## Vea también  
 [Crear características de SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Cómo: Personalizar una característica de SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Cómo: Agregar y quitar elementos de las características de SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [NIB: Building SharePoint Solutions with Team Foundation Server](http://msdn.microsoft.com/es-es/700a570a-e98e-4425-aadd-34c014868d43)  
  
  
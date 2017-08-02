---
title: "C&#243;mo: Agregar y quitar carpetas asignadas"
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
  - "VS.SharePointTools.Project.MappedFolder"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "carpetas asignadas [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, carpetas asignadas"
ms.assetid: 115c8b00-7d4c-4fbe-b42c-e82dca944504
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# C&#243;mo: Agregar y quitar carpetas asignadas
  Algunas carpetas de uso común en SharePoint, como Imágenes y diseños, se insertan de profundidad en la jerarquía de archivos.  Puede asignar estas carpetas en un proyecto SharePoint para tener acceso más fácilmente a ellas.  Las carpetas asignadas son carpetas del proyecto SharePoint que corresponden a la ubicación física de los archivos en el Servidor de SharePoint.  
  
 Al implementar una aplicación de SharePoint, el contenido de la carpeta asignada y todas sus subcarpetas por el paquete de solución \(.wsp\) sobre el servidor que está ejecutando SharePoint en la ubicación especificada en el árbol de carpetas de SharePoint.  Esta ubicación viene determinada por la propiedad de **Deployment Location** que se establece para la carpeta asignada.  Cualquier subcarpeta de la carpeta asignada es **Deployment Location** con respecto a la carpeta asignada.  Observe que la propiedad de **Deployment Location** , no el nombre de la carpeta asignada, determina dónde se implementan los elementos.  
  
 Puede agregar carpetas asignadas a un proyecto utilizando los comandos de la barra de menús o menú contextual para el proyecto.  Puede utilizar los comandos de **Agregue la carpeta asignada “las imágenes” de SharePoint** y de **Agregue la carpeta “layouts” de SharePoint** de agregar las carpetas asignadas que se utilizan con más frecuencia.  Puede asignar cualquiera de las otras carpetas disponibles de SharePoint al proyecto mediante el comando de **Agregar carpeta asignada de SharePoint** en el menú contextual y luego especificar las carpetas en el cuadro de diálogo de **Agregar carpeta asignada de SharePoint** .  
  
## Agregar carpetas asignadas a un proyecto  
 El procedimiento siguiente describe cómo agregar dos carpetas asignadas a un proyecto web visual de la parte.  Para empezar, debe crear un proyecto web visual de la parte.  
  
#### Para agregar carpetas asignadas a un proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el cuadro de diálogo de **Nuevo proyecto** , expanda **Visual Basic** o el nodo de **Visual C\#** , expanda el nodo de **Office\/SharePoint** y, a continuación el nodo de **Soluciones de SharePoint** .  
  
3.  En la lista de plantillas de proyecto, elija la plantilla de **Elemento web visual de SharePoint 2013** .  
  
4.  En el cuadro de **Name** , escriba TestProject1, y elija el botón de **Aceptar** .  
  
5.  En **Asistente para la personalización de SharePoint**, elija el botón de **Finalizar** para conservar la configuración predeterminada.  
  
6.  En **Explorador de soluciones**, elija el nodo de proyecto y, a continuación, en la barra de menús, elija **Project**, **Agregue la carpeta asignada “las imágenes” de SharePoint**.  
  
     Una carpeta que se denomina **Imágenes** aparece en el proyecto y contiene una subcarpeta denominada TestProject1.  Esta carpeta asignada contendrá las imágenes para el proyecto web visual de la parte.  
  
7.  En **Explorador de soluciones**, elija el nodo de proyecto y, a continuación, en la barra de menús, elija **Project**, **Agregar carpeta asignada de SharePoint** para mostrar el cuadro de diálogo de **Agregar carpeta asignada de SharePoint** .  
  
8.  En la vista de árbol de las carpetas disponibles para asignar, elija la carpeta de **recursos** , y elija el botón de **Aceptar** .  
  
     Una carpeta que se denomina **recursos** aparece en el proyecto.  Esta carpeta puede almacenar los elementos como archivos de recursos de cadena.  Las Sub\- carpetas pueden resultar útiles para organizar el contenido de una carpeta asignada, pero no se crean automáticamente al agregar una carpeta asignada mediante el comando de **Agregar carpeta asignada de SharePoint** .  Para agregar una sub\- carpeta, elija la carpeta de **recursos** y, a continuación, en la barra de menús, elija **Project**, **Nueva carpeta**.  
  
## Cambiar la ubicación de implementación de una carpeta asignada  
 De forma predeterminada, las carpetas asignadas se agregan a ubicaciones específicas en relación con la ruta de instalación raíz de SharePoint, que el token {SharePointRoot} indica.  Sin embargo, se puede cambiar esta ubicación estableciendo la propiedad **Deployment location** de la carpeta asignada.  Cada carpeta asignada tiene su propia propiedad **Deployment location**.  
  
#### Para cambiar la ubicación de implementación de una carpeta asignada  
  
1.  En el proyecto que creó anteriormente, elija una carpeta asignada.  
  
2.  En la ventana de **Propiedades** , elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\) de la propiedad de **Deployment location** .  
  
3.  En el cuadro de diálogo de **Agregar carpeta asignada de SharePoint** , vaya a la carpeta que desea que la carpeta asignada para los informes.  
  
4.  Elija el nodo, y elija el botón de **Aceptar** .  
  
## Quitar o cambiar el nombre de las carpetas asignadas  
  
#### Para cambiar el nombre o quitar una carpeta asignada  
  
1.  En el proyecto que creó anteriormente, elija una carpeta asignada.  
  
2.  Para cambiar el nombre de la carpeta asignada, abra el menú contextual, elija **Rename**, escriba el nuevo nombre, y elija la tecla ENTRAR.  
  
     Como alternativa, puede elegir la carpeta asignada cuyo nombre desea cambiar, abra la ventana de **Propiedades** , y establezca el valor de la propiedad de **Folder name** al nuevo nombre.  
  
3.  Para quitar una carpeta asignada del proyecto, abra el menú contextual, elija **Suprimir**, y elija el botón de **Aceptar** en el cuadro de diálogo para confirmar la eliminación.  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  
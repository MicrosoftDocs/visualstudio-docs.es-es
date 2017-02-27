---
title: "Mostrar archivos mediante el comando Abrir archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipos de proyecto, compatibilidad con el comando Abrir archivo"
  - "Abrir archivo (comando)"
  - "persistencia, compatibilidad con el comando Abrir archivo"
ms.assetid: 4fff0576-b2f3-4f17-9769-930f926f273c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Mostrar archivos mediante el comando Abrir archivo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los pasos siguientes describen cómo el IDE administra el comando de **Abrir archivo** , que está disponible en el menú de **Archivo** en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Los pasos describen cómo los proyectos deben responder a las llamadas que se originen desde este comando.  
  
 Cuando un usuario hace clic en el comando de **Abrir archivo** en el menú de **Archivo** , y selecciona un archivo del cuadro de diálogo de **Abrir archivo** , el proceso siguiente aparece.  
  
1.  Utilizando la tabla en el documento, el IDE determina si el archivo está abierto en un proyecto.  
  
    -   Si el archivo está abierto, el IDE vuelve a mejorar el la ventana.  
  
    -   Si el archivo no está abierto, el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> para ver cada proyecto de determinar qué proyecto puede abrir el archivo.  
  
        > [!NOTE]
        >  En la ejecución del proyecto de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>, proporcione un valor de prioridad que indica el nivel en el que el proyecto se abrirá el archivo.  los valores de prioridad se proporcionan en la enumeración de <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> .  
  
2.  Cada proyecto responde con un nivel de prioridad que indique la importancia que coloca en como proyecto abrir el archivo.  
  
3.  El IDE utiliza los siguientes criterios para determinar abra qué proyecto el archivo:  
  
    -   El proyecto que responde con prioridad máxima \(DP\_Intrinsic\) abra el archivo.  Si más de un proyecto responde con esta prioridad, el primer proyecto de responder abrirá el archivo.  
  
    -   Si ningún proyecto responde con prioridad máxima \(DP\_Intrinsic\), pero todos los proyectos responden con el mismo, menor prioridad, el proyecto activo abrirá el archivo.  Si no hay ningún proyecto activo, el primer proyecto de responder abrirá el archivo.  
  
    -   Si ningún proyecto petición la propiedad del archivo \(DP\_Unsupported\), el proyecto de archivos varios abrirá el archivo.  
  
         Si una instancia del proyecto de archivos varios se crea, el proyecto responde siempre el valor DP\_CanAddAsExternal.  este valor indica que el proyecto puede abrir el archivo.  Se utiliza este proyecto de contener abrir archivos que no están en ningún otro proyecto.  La lista de elementos de este proyecto no se conserva; este proyecto está visible en **Explorador de soluciones** únicamente cuando se usa para abrir un archivo.  
  
         Si el proyecto de archivos varios no indica que puede abrir el archivo, una instancia de proyecto no se ha creado.  En este caso, el IDE crea una instancia del proyecto de archivos varios y indica el proyecto para abrir el archivo.  
  
4.  En cuanto el IDE determine abra qué proyecto el archivo, llama al método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> en ese proyecto.  
  
5.  El proyecto podrá obtener la opción para abrir el archivo con un editor específico del proyecto o un editor estándar.  Para obtener más información, vea [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md) y [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md) respectivamente.  
  
## Vea también  
 [Visualización de archivos mediante el abrir con el comando](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)   
 [Abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Cómo: abrir editores específicos del proyecto](../../extensibility/how-to-open-project-specific-editors.md)   
 [Cómo: abrir editores estándares](../../extensibility/how-to-open-standard-editors.md)
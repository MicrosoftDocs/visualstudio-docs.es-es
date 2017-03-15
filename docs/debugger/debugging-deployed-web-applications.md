---
title: "Depurar aplicaciones web implementadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "aplicaciones web ASP.NET"
  - "ASP.NET, depurar aplicaciones web"
  - "depurar servicios Web"
  - "servicios Web, depurar"
  - "servicios Web XML, depurar"
  - "XML, depurar servicios Web"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 31
---
# Depurar aplicaciones web implementadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si tiene que depurar una aplicación web se ejecuta en un servidor de producción, debería hacerlo con precaución.  Si establece una asociación al proceso de trabajo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] para depurar y alcanza un punto de interrupción, por ejemplo, se detendrá todo el código administrado del proceso de trabajo.  Detener todo el código administrado del proceso de trabajo puede interrumpir el trabajo de todos los usuarios del servidor.  Antes de depurar en un servidor de producción, considere los posibles efectos que tendrá en el trabajo de producción.  
  
 Para usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a fin de depurar una aplicación implementada, debe establecer una asociación al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] y asegurarse de que el depurador tiene acceso a los símbolos de la aplicación.  También debe buscar y abrir los archivos de código fuente de la aplicación.  Para obtener más información, vea [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Cómo: Buscar el nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) y [Requisitos del sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Muchas aplicaciones web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hacen referencia a archivos DLL que contienen lógica empresarial u otro código de utilidad.  Dicha referencia copia automáticamente el archivo DLL del equipo local a la carpeta \\bin del directorio virtual de la aplicación web.  Durante el proceso de depuración, recuerde que la aplicación web hace referencia a esa copia del archivo DLL y no a la copia del equipo local.  
  
 El procedimiento para asociarse al proceso de trabajo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] es el mismo que para asociarse a cualquier otro proceso remoto.  Cuando está asociado, si no tiene abierto el proyecto correcto, aparecerá un cuadro de diálogo cuando se interrumpa la aplicación.  Este cuadro de diálogo pide la ubicación de los archivos de código fuente de la aplicación.  El nombre de archivo que especifique en el cuadro de diálogo debe coincidir con el nombre especificado en los símbolos de depuración, ubicados en el servidor web.  Para obtener más información, vea [Crear asociaciones con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## Vea también  
 [Depurar aplicaciones ASP.NET y aplicaciones habilitadas para AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Depurar script y aplicaciones web](../debugger/debugging-web-applications-and-script.md)   
 [Cómo: Habilitar la depuración de aplicaciones de ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Cómo: Buscar el nombre de un proceso de ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
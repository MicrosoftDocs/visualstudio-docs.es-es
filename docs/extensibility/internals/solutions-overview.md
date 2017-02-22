---
title: "Informaci&#243;n general sobre soluciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "soluciones, acerca de las soluciones"
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Informaci&#243;n general sobre soluciones
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Una solución es una agrupación de uno o varios proyectos que funcionan conjuntamente para crear una aplicación. La información del proyecto y el estado correspondiente a la solución se almacenan en dos archivos de solución diferente. El archivo de solución \(.sln\) está basado en texto y pueden situados bajo control de código fuente y se comparten los usuarios. El archivo de opción \(.suo\) de usuario de solución es binario. Como resultado, el archivo .suo no se puede colocar en el control de código fuente y contiene información específica del usuario.  
  
 Puede escribir cualquier VSPackage en cualquier tipo de archivo de solución. Debido a la naturaleza de los archivos, hay dos interfaces diferentes que se implementan para escribir en ellos. El <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaz escribe información de texto en el archivo .sln y <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> interfaz escribe secuencias binarias en el archivo .suo.  
  
> [!NOTE]
>  Un proyecto no tiene que escribir explícitamente una entrada para sí mismo en el archivo de solución el entorno controla el proyecto. Por lo tanto, a menos que desee agregar contenido adicional específicamente para el archivo de solución, no es necesario registrar el VSPackage de esta manera.  
  
 Cada VSPackage compatible con la persistencia de la solución usa tres interfaces, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaz, que es implementada por el entorno y llama el VSPackage, y `IVsPersistSolutionProps` y `IVsPersistSolutionOpts`, que son ambos implementados por el VSPackage. El `IVsPersistSolutionOpts` interfaz sólo debe implementarse si se escribirá el VSPackage al archivo .suo información privada.  
  
 Cuando se abre una solución, el proceso siguiente tiene lugar.  
  
1.  El entorno lee la solución.  
  
2.  Si el entorno se encuentra un `CLSID`, carga el VSPackage correspondiente.  
  
3.  Si se carga un paquete VSPackage, el entorno llama `QueryInterface` para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> interfaz para la interfaz que requiere el VSPackage.  
  
    1.  Al leer desde un archivo .sln, el entorno llama `QueryInterface` para `IVsPersistSolutionProps`.  
  
    2.  Al leer desde un archivo .suo, el entorno llama `QueryInterface` para `IVsPersistSolutionOpts`.  
  
 Información específica sobre el uso de estos archivos se puede encontrar en [Solución \(. Archivo sln\)](../../extensibility/internals/solution-dot-sln-file.md) y [Opciones de usuario de solución \(. Archivo suo\)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Si desea crear una nueva configuración de solución que consta de las configuraciones de dos de los proyectos y excluir un tercio de la compilación, debe utilizar la interfaz de usuario de las páginas de propiedad o la automatización. No se puede cambiar las configuraciones de administrador de compilación de soluciones y sus propiedades directamente, pero se puede manipular mediante el Administrador de la compilación de soluciones la `SolutionBuild` clase a partir de DTE del modelo de automatización. Para obtener más información acerca de la configuración de soluciones, consulte [Configuración de soluciones](../../extensibility/internals/solution-configuration.md).  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
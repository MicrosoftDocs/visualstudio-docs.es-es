---
title: Iniciar una compilación desde el IDE | Microsoft Docs
description: Aprenda a usar Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor para iniciar compilaciones para sistemas de proyectos personalizados.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- build
ms.assetid: 936317aa-63b7-4eb0-b9db-b260a0306196
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ee685ebf542dbf9405afce8cfdf5c4a7e060b79
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956053"
---
# <a name="start-a-build-from-within-the-ide"></a>Iniciar una compilación desde el IDE

Los sistemas de proyectos personalizados deben utilizar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildManagerAccessor> para iniciar las compilaciones. En este artículo se describen las razones de este requisito y se examina el procedimiento.

## <a name="parallel-builds-and-threads"></a>Compilaciones y subprocesos paralelos

 Visual Studio permite compilaciones paralelas, que requieren mediación para tener acceso a los recursos comunes. Los sistemas de proyectos pueden ejecutar compilaciones de forma asincrónica, pero tales sistemas no deben llamar a las funciones de compilación desde dentro de las devoluciones de llamadas.

 Si el sistema de proyectos modifica las variables de entorno, debe establecer el valor de NodeAffinity de la compilación en OutOfProc. Este requisito significa que no se pueden utilizar objetos host, puesto que requieren el nodo in-proc.

## <a name="use-ivsbuildmanageraccessor"></a>Uso de IVSBuildManagerAccessor

 En el siguiente código se describe un método que un sistema de proyectos puede utilizar para iniciar una compilación:

```csharp

public bool Build(Project project, bool isDesignTimeBuild)
{
    // Get the accessor from the IServiceProvider interface for the
    // project system
    IVsBuildManagerAccessor accessor =
        serviceProvider.GetService(typeof(SVsBuildManagerAccessor)) as
        IVsBuildManagerAccessor;
    bool releaseUIThread = false;
    try
    {
        if(accessor != null)
        {
            // Claim the UI thread under the following conditions:
            // 1. The build must use a resource that uses the UI thread
            // or,
            // 2. The build requires the in-proc node AND waits on the
            // UI thread for the build to complete
            if(NeedsUIThread)
            {
                int result = accessor.ClaimUIThreadForBuild();
                if(result != S_OK)
                {
                     // Not allowed to claim the UI thread right now
                     return false;
                }
                releaseUIThread = true;
             }
             if(isDesignTimeBuild)
             {
// Start the design time build
                  int result = accessor.BeginDesignTimeBuild();
                  if(result != S_OK)
                  {
                      // Not allowed to begin a design-time build at
                      // this time. Try again later.
                      return false;
                  }
             }
         }
         bool buildSucceeded = false;
         // perform project-system specific build set up tasks
         // Create your BuildRequestData
         // This assumes a IHostServices variable (hostServices) set
   // to your host services. If you don't use a project instance
         // (you build from a file for example) then use another
         // constructor.
         BuildRequestData requestData = new
             BuildRequestData(project.CreateProjectInstance(),
             "myTarget", hostServices,
             BuildRequestData.BuildRequestDataFlags.None);
         // Mark your your submission as Pending
         BuildSubmission submission =
              BuildManager.DefaultBuildManager.
              PendBuildRequest(requestData);
         // Register the loggers in BuildLoggers
         if (accessor != null)
         {
               foreach (ILogger logger in BuildLoggers)
               {
                    accessor.RegisterLogger(submission.SubmissionId,
                        logger);
               }
         }
         BuildResult buildResult = submission.Execute();
         return buildResult;
     }
     // Clean up resources
     finally
     {
         if(accessor != null)
         {
             // Unregister the loggers, if necessary.
             accessor.UnregisterLoggers(submission.SubmissionId);
             // Release the UI thread, if used
             if(releaseUIThread)
             {
                  accessor.ReleaseUIThreadForBuild();
             }
             // End the design time build, if used
             if(isDesignTimeBuild)
             {
                  accessor.EndDesignTimeBuild();
             }
         }
     }
}
```

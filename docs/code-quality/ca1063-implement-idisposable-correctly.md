---
title: "CA1063: Implemente IDisposable correctamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063: Implemente IDisposable correctamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|Identificador de comprobación|CA1063|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 `IDisposable` no se ha implementado correctamente.  Algunas causas de este problema se muestran aquí:  
  
-   IDisposable se implementa de nuevo en la clase.  
  
-   Se vuelve a reemplazar Finalice.  
  
-   Se reemplaza Dispose.  
  
-   Dispose\(\) no es público, no está sellado o se denomina Dispose.  
  
-   Dispose\(bool\) no está protegido o sellado, o no es virtual.  
  
-   En tipos no sellados, Dispose\(\) debe llamar a Dispose\(true\).  
  
-   Para los tipos no sellados, la implementación de Finalice no llama Dispose\(bool\), al finalizador de la clase de caso, o a ambos.  
  
 La infracción de cualquiera de estos modelos desencadenará esta advertencia.  
  
 Cada tipo IDisposable de raíz no sellada debe proporcionar su propio método Dispose\(bool\) vacío virtual protegido.  Dispose\(\) debe llamar a Dispose\(true\) y Finalize debe llamar a Dispose\(false\).  Si va a crear un tipo IDisposable de raíz no sellada, debe definir Dispose\(bool\) y llamarlo.  Para obtener más información, vea la sección [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md) y [Instrucciones de diseño de Framework](../Topic/Framework%20Design%20Guidelines.md) en la documentación de .NET Framework.  
  
## Descripción de la regla  
 Todos los tipos IDisposable deben implementar el modelo de Dispose correctamente.  
  
## Cómo corregir infracciones  
 Examine su código y determine cuál de las resoluciones siguientes corregirá esta infracción.  
  
-   Quite IDisposable de la lista de interfaces implementada por {0} y, en su lugar, reemplace la implementación de Dispose de la clase base.  
  
-   Quite el finalizador del tipo {0}, reemplace Dispose\(bool disposing\) y coloque la lógica de finalización en la ruta de acceso del código donde 'disposing' es false.  
  
-   Quite {0}, reemplace Dispose\(bool disposing\) y coloque la lógica de Dispose en la ruta de acceso del código donde 'disposing' es true.  
  
-   Asegúrese de que {0} se declare como público y sellado.  
  
-   Cambie el nombre de {0} por 'Dispose' y asegúrese de que se declara como público y sellado.  
  
-   Asegúrese de que {0} se declara como protegido, virtual y no sellado.  
  
-   Modifique {0} de modo que llame a Dispose\(true\), llame a GC.SuppressFinalize en la instancia de objeto actual \('this' o 'Me' en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) y, a continuación, vuelva.  
  
-   Modifique {0} para que llame a Dispose\(false\) y, a continuación, vuelva.  
  
-   Si está escribiendo una clase raíz IDisposable no sellada, asegúrese de que la implementación de IDisposable sigue el modelo que se describe anteriormente en esta sección.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo de seudocódigo  
 En el pseudocódigo siguiente se proporciona un ejemplo general de cómo se debe implementar Dispose\(bool\) en una clase que utiliza recursos administrados y nativos.  
  
```  
public class Resource : IDisposable   
{  
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);  
    private AnotherResource managedResource = new AnotherResource();  
  
// Dispose() calls Dispose(true)  
    public void Dispose()  
    {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
    // NOTE: Leave out the finalizer altogether if this class doesn't   
    // own unmanaged resources itself, but leave the other methods  
    // exactly as they are.   
    ~Resource()   
    {  
        // Finalizer calls Dispose(false)  
        Dispose(false);  
    }  
    // The bulk of the clean-up code is implemented in Dispose(bool)  
    protected virtual void Dispose(bool disposing)  
    {  
        if (disposing)   
        {  
            // free managed resources  
            if (managedResource != null)  
            {  
                managedResource.Dispose();  
                managedResource = null;  
            }  
        }  
        // free native resources if there are any.  
        if (nativeResource != IntPtr.Zero)   
        {  
            Marshal.FreeHGlobal(nativeResource);  
            nativeResource = IntPtr.Zero;  
        }  
    }  
}  
```
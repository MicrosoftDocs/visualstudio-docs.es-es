---
title: "CA2153: Evitar el control de excepciones de estado dañadas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: eabddaea271eb07873fc50bd4824a5108514444c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: Evitar el control de excepciones de estado dañadas
|||  
|-|-|  
|TypeName|AvoidHandlingCorruptedStateExceptions|  
|Identificador de comprobación|CA2153|  
|Categoría|Microsoft.Security|  
|Cambio problemático|No trascendental|  
  
## <a name="cause"></a>Motivo  
 Las[excepciones de estado dañado (CSE)](https://msdn.microsoft.com/en-us/magazine/dd419661.aspx) indican que la memoria está dañada en el proceso. Detectar estos problemas y evitar el bloqueo del proceso puede provocar vulnerabilidades de seguridad si un atacante puede colocar una vulnerabilidad de seguridad en la región de memoria dañada.  
  
## <a name="rule-description"></a>Descripción de la regla  
 CSE indica que el estado de un proceso se ha dañado y el sistema no lo ha detectado. En el escenario de estado dañado, un controlador general solo detecta la excepción si se marca el método con el atributo `HandleProcessCorruptedStateExceptions` correcto. De forma predeterminada, [Common Language Runtime (CLR)](https://msdn.microsoft.com/en-us/library/8bs2ecf4.aspx) no invocará controladores catch de CSE.  
  
 Permitir el bloqueo del proceso sin detectar estos tipos de excepciones es la opción más segura, ya que incluso el registro del código puede permitir a los atacantes aprovechar errores de memoria dañada.  
  
 Esta advertencia se desencadena cuando se detectan CSE con un controlador general que detecta todas las excepciones, como catch (excepción) o catch (sin especificación de excepción).  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para resolver esta advertencia debe realizar una de las acciones siguientes:  
  
 1. Quitar el `HandleProcessCorruptedStateExceptions` atributo. Esto revierte el comportamiento de tiempo de ejecución predeterminado en el que las CSE no se pasan a los controladores catch.  
  
 2. Quite el controlador catch general y use controladores que capturen tipos de excepción específicos.  Esto puede incluir CSE suponiendo que el código del controlador puede controlarlas de manera segura (caso poco frecuente).  
  
 3. Vuelva a producir el CSE en el controlador catch, lo que garantiza que la excepción se pasará al que realiza la llamada y dará como resultado la finalización del proceso en ejecución.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo  
  
### <a name="violation"></a>Infracción  
 El pseudocódigo siguiente muestra el patrón que detecta esta regla.  
  
```  
[HandleProcessCorruptedStateExceptions]   
//method to handle and log CSE exceptions   
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (Exception e)  
    {  
        // Handle error  
    }  
}  
```  
  
### <a name="solution-1"></a>Solución 1  
 Quitar el atributo HandleProcessCorruptedExceptions garantiza que las excepciones no se controlarán.  
  
```  
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (IOException e)  
    {  
        // Handle error  
    }  
    catch (UnauthorizedAccessException e)  
    {  
        // Handle error  
    }  
}  
```  
  
### <a name="solution-2"></a>Solución 2  
 Quite el controlador catch general y detecte solo los tipos determinados de excepción.  
  
```  
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (IOException e)  
    {  
        // Handle error  
    }  
    catch (UnauthorizedAccessException e)  
    {  
        // Handle error  
    }  
}  
```  
  
### <a name="solution-3"></a>Solución 3  
 Vuelva a generar la excepción.  
  
```  
void TestMethod1()   
{   
    try  
    {  
        FileStream fileStream = new FileStream("name", FileMode.Create);  
    }    
    catch (Exception e)  
    {  
        // Handle error  
        throw;  
    }  
}  
```
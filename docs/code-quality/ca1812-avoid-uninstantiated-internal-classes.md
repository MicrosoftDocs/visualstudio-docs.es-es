---
title: "CA1812: Evitar las clases internas sin instancia | Microsoft Docs"
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
  - "CA1812"
  - "AvoidUninstantiatedInternalClasses"
helpviewer_keywords: 
  - "AvoidUninstantiatedInternalClasses"
  - "CA1812"
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1812: Evitar las clases internas sin instancia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUninstantiatedInternalClasses|  
|Identificador de comprobación|CA1812|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 El código del ensamblado no crea una instancia del tipo del nivel de ensamblado.  
  
## Descripción de la regla  
 Esta regla intenta buscar una llamada a uno de los constructores del tipo, y crea un informe sobre una infracción si no se encuentra ninguna llamada.  
  
 Esta regla no examina los siguientes tipos:  
  
-   Tipos de valor  
  
-   Tipos abstractos  
  
-   Enumeraciones  
  
-   Delegados  
  
-   Tipos de matriz emitidos por el compilador  
  
-   Tipos de los que no se pueden crear instancias y que solo definen métodos estáticos `static` \(`Shared` en Visual Basic\).  
  
 Si aplica <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> al ensamblado que se está analizando, esta regla no ocurrirá en los constructores marcados como `internal` porque no se puede saber si otro ensamblado de `friend` está utilizando un campo.  
  
 Aunque no se pueda evitar esta limitación en el análisis de código de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], el FxCop independiente externo se producirá en constructores internos si cada ensamblado `friend` se encuentra en el análisis.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el tipo o agregue el código que lo utiliza.  Si el tipo sólo contiene métodos estáticos, agregue uno de los siguientes al tipo para evitar que el compilador emita un constructor de instancia público predeterminado:  
  
-   Un constructor privado para tipos diseñados para las versiones 1.0 y 1.1 de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   El modificador `static` \(`Shared` en Visual Basic\) de los tipos diseñados para [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  Recomendamos que suprima esta advertencia en las situaciones siguientes:  
  
-   La clase se crea a través de métodos de reflexión enlazados en tiempo de ejecución, como <xref:System.Activator.CreateInstance?displayProperty=fullName>.  
  
-   La clase se crea automáticamente por el runtime o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Por ejemplo, las clases que implementan <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> o <xref:System.Web.IHttpHandler?displayProperty=fullName>.  
  
-   La clase se pasa como un parámetro de tipo genérico que tiene una nueva restricción.  Por ejemplo, el ejemplo siguiente provocará esta regla:  
  
    ```c#  
    internal class MyClass  
    {     
        public DoSomething()     
        {  
        }  
    }   
    public class MyGeneric<T> where T : new()  
    {  
        public T Create()  
        {  
            return new T();     
        }  
    }  
    // [...]   
    MyGeneric<MyClass> mc = new MyGeneric<MyClass>();  
    mc.Create();  
    ```  
  
 En estas situaciones, recomendamos que suprima esta advertencia.  
  
## Reglas relacionadas  
 [CA1811: Evitar código privado al que no se llama](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1801: Revisar parámetros sin utilizar](../code-quality/ca1801-review-unused-parameters.md)  
  
 [CA1804: Quitar variables locales no utilizadas](../code-quality/ca1804-remove-unused-locals.md)
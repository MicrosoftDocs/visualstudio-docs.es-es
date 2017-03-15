---
title: "Utilizar el atributo DebuggerTypeProxy | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
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
  - "atributos [C#], depurador"
  - "DebuggerTypeProxy (atributo)"
  - "DebuggerTypeProxyAttribute (clase)"
ms.assetid: 943f3bb1-993e-4800-a47e-0af78b063014
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Utilizar el atributo DebuggerTypeProxy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerTypeProxyAttribute> especifica un proxy, o suplente, para un tipo y cambia la forma en que se muestra el tipo en las ventanas del depurador.  Cuando se ve una variable que tiene un proxy, el proxy reemplaza al tipo original en la **presentación**.  En la ventana de las variables del depurador se muestran sólo los miembros públicos del tipo de servidor proxy.  No se muestran los miembros privados.  
  
 Este atributo se puede aplicar a:  
  
-   Estructuras  
  
-   Clases  
  
-   Ensamblados  
  
 Una clase de proxy de tipo debe tener un constructor que tome un argumento del tipo que el proxy reemplazará.  El depurador crea una nueva instancia de la clase de proxy de tipo cada vez que necesita mostrar una variable del tipo de destino.  Esto puede afectar al rendimiento.  Por tanto, en el constructor no debe realizarse más trabajo del estrictamente necesario.  
  
 Para minimizar la reducción de rendimiento, el evaluador de expresiones no examina los atributos en el proxy de presentación del tipo, a menos que el usuario expanda el tipo haciendo clic en el símbolo \+ en la ventana del depurador o mediante <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  Por consiguiente, no se deben colocar atributos en el propio tipo de presentación.  Los atributos pueden y deben utilizarse en el cuerpo del tipo de presentación.  
  
 Se recomienda que el proxy de tipo sea una clase anidada privada dentro de la clase que el atributo tiene como destino.  De este modo, puede obtener acceso fácilmente a los miembros internos.  
  
 Si se utiliza <xref:System.Diagnostics.DebuggerTypeProxyAttribute> en el nivel de ensamblado, el parámetro `Target` especifica el tipo que reemplazará el proxy.  
  
 Para obtener un ejemplo de cómo utilizar este atributo junto con los atributos <xref:System.Diagnostics.DebuggerDisplayAttribute> y <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, vea [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
## Utilizar genéricos con DebuggerTypeProxy  
 La compatibilidad con los genéricos es limitada.  En C\#, `DebuggerTypeProxy` solo acepta tipos abiertos.  Un tipo abierto, también denominado tipo no construido, es un tipo genérico de cuyos parámetros de tipo no se han creado instancias con argumentos.  No se admiten los tipos cerrados, también denominados tipos construidos.  
  
 La sintaxis de un tipo abierto tiene el siguiente aspecto:  
  
 `Namespace.TypeName<,>`  
  
 Si utiliza un tipo genérico como destino en `DebuggerTypeProxy`, debe utilizar esta sintaxis.  El mecanismo `DebuggerTypeProxy` deduce los parámetros de tipo automáticamente.  
  
 Para obtener más información sobre los tipos abiertos y cerrados en C\#, vea la [Especificación del lenguaje C\#](/dotnet/csharp/language-reference/language-specification), sección 20.5.2 Tipos abiertos y cerrados.  
  
 Visual Basic no tiene sintaxis de tipos abiertos, por lo que no se puede hacer lo mismo en Visual Basic.  En su lugar, debe utilizar una representación de cadena del nombre del tipo abierto.  
  
 `"Namespace.TypeName'2"`  
  
## Vea también  
 [Usar el atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Mostrar tipos de datos personalizados](../debugger/create-custom-views-of-dot-managed-objects.md)   
 [Enhancing Debugging with the Debugger Display Attributes](../Topic/Enhancing%20Debugging%20with%20the%20Debugger%20Display%20Attributes.md)
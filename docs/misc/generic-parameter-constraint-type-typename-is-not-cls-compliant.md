---
title: "El tipo de restricci&#243;n de par&#225;metro gen&#233;rico &lt;typename&gt; no es conforme con CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40040"
  - "vbc40040"
helpviewer_keywords: 
  - "BC40040"
ms.assetid: c640dd59-56a9-43ed-b199-32a60f7b9b06
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo de restricci&#243;n de par&#225;metro gen&#233;rico &lt;typename&gt; no es conforme con CLS
Un tipo genérico está marcado como `<CLSCompliant(True)>`, pero una restricción en uno de sus parámetros de tipo especifica un tipo que está marcado como `<CLSCompliant(False)>`, no está marcado o no cumple los requisitos porque es un tipo que no conforme.  
  
 Para que un tipo sea compatible con [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), debe utilizar solo tipos conformes con CLS. Esto se aplica también a las restricciones en los parámetros de tipo de un tipo genérico.  
  
 Los siguientes tipos de datos [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no son conformes con CLS:  
  
-   [SByte \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/sbyte-data-type)  
  
-   [UInteger \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/uinteger-data-type)  
  
-   [ULong \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/ulong-data-type)  
  
-   [UShort \(Tipo de datos\)](/dotnet/visual-basic/language-reference/data-types/ushort-data-type)  
  
 Al aplicar el atributo <xref:System.CLSCompliantAttribute> a un elemento de programación, establezca el parámetro `isCompliant` del atributo como `True` o `False` para indicar compatibilidad o incompatibilidad. No hay ningún valor predeterminado para este parámetro y debe proporcionar un valor.  
  
 Si no aplica <xref:System.CLSCompliantAttribute> a un elemento, se considera que no es conforme.  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Id. de error:** BC40040  
  
### Para corregir este error  
  
-   Si el tipo genérico debe tomar un parámetro de tipo restringido por este tipo determinado, quite <xref:System.CLSCompliantAttribute>. El tipo no puede ser conforme con CLS.  
  
-   Si el tipo genérico debe ser conforme con CLS, cambie el tipo de esta restricción al tipo compatible con CLS más próximo. Por ejemplo, en lugar de `UInteger`, quizá pueda usar `Integer` si no necesita que el intervalo de valores esté por encima de 2.147.483.647. Si necesita el intervalo extendido, puede reemplazar `UInteger` por `Long`.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [\<PAVE OVER\> Escribir código conforme con CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
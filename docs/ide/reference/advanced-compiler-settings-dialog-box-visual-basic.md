---
title: "Configuración de compilador avanzada (Cuadro de diálogo, Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords: Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6fce612245c07cf3bcd70b56b266857db88765d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Configuración de compilador avanzada (Cuadro de diálogo, Visual Basic)
Use el cuadro de diálogo **Configuración de compilación avanzada** del **Diseñador de proyectos** para especificar las propiedades de configuración de compilación avanzada del proyecto. Este cuadro de diálogo solo se aplica a proyectos de Visual Basic.  
  
### <a name="to-access-this-dialog-box"></a>Para obtener acceso a este cuadro de diálogo  
  
1.  En el **Explorador de soluciones**, elija el nodo de proyecto (no el nodo **Solución**).  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Compilar**.  
  
3.  En la [página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), seleccione **Configuración** y **Plataforma**. En las configuraciones de compilación simplificadas, no se muestran las listas **Configuración** y **Plataforma**. Para obtener más información, consulte [Configuraciones Debug y Release](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
4.  Haga clic en **Opciones de compilación avanzadas**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="optimizations"></a>Optimizaciones  
 Las opciones siguientes especifican optimizaciones que, en algunos casos, permiten reducir un archivo de programa, acelerar la ejecución de un programa o acelerar el proceso de compilación.  
  
 **Quitar comprobaciones de desbordamiento con enteros**  
 De manera predeterminada, esta casilla está desactivada para habilitar la comprobación de desbordamiento con enteros. Actívela para dejar de comprobar el desbordamiento con enteros. Si selecciona esta casilla, los cálculos de enteros pueden ser más rápidos. Sin embargo, si cancela la comprobación de desbordamiento y las capacidades de tipo de datos desbordan, puede ser que se almacenen resultados incorrectos sin que se emita ningún error.  
  
 Si se marcan las condiciones de desbordamiento y una operación de enteros desborda, se produce una excepción <xref:System.OverflowException>. Si las condiciones de desbordamiento no se marcan, los desbordamientos de operación de enteros no indican ninguna excepción.  
  
 **Habilitar optimizaciones**  
 De manera predeterminada, esta casilla está desactivada para deshabilitar las optimizaciones del compilador. Actívela para habilitar las optimizaciones del compilador. Gracias a las optimizaciones del compilador, el archivo de salida será más pequeño, más rápido y más eficaz. Sin embargo, puesto que las optimizaciones provocan una reorganización de código en el archivo de salida, las optimizaciones del compilador pueden dificultar la depuración.  
  
 **Dirección base del archivo DLL**  
 En este cuadro de texto se muestra la dirección base predeterminada del archivo DLL en formato hexadecimal. En los proyectos de biblioteca de clases y biblioteca de controles, puede usar este cuadro de texto para especificar la dirección base que se usará al crear el archivo DLL.  
  
 **Generar información de depuración**  
 Seleccione **Ninguna**, **Completa** o **Solo PDB** en la lista. **Ninguna** especifica que no se genera ninguna información de depuración. **Completa** especifica que se genera información de depuración completa y **Solo PDB** especifica que se genera únicamente información de depuración PDB. De manera predeterminada, el valor de esta opción es **Completa**.  
  
## <a name="compilation-constants"></a>Constantes de compilación  
 Las constantes de compilación condicionales tienen un efecto parecido al de usar una directiva de preprocesador [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) en un archivo de origen, salvo por el hecho de que las constantes definidas son públicas y se aplican a todos los archivos del proyecto. Puede usar las constantes de compilación condicional junto con la directiva [#If...Then...#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) para compilar condicionalmente archivos de origen. Consulte [Compilación condicional](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Definir constante DEBUG**  
 De manera predeterminada, esta casilla está activada, lo que indica que se establece una constante DEBUG.  
  
 **Definir constante TRACE**  
 De manera predeterminada, esta casilla está activada, lo que indica que se establece una constante TRACE.  
  
 **Constantes personalizadas**  
 Escriba una de estas constantes personalizada para su aplicación en este cuadro de texto. Las entradas deben estar delimitadas por comas, con este formato: **Nombre1="Valor1",Nombre2="Valor2",Nombre3="Valor3"**.  
  
## <a name="other-settings"></a>Otras configuraciones  
 **Generar ensamblados de serialización**  
 Esta configuración especifica si el compilador creará ensamblados de serialización XML. Los ensamblados de serialización pueden mejorar el rendimiento de inicio de <xref:System.Xml.Serialization.XmlSerializer> si ha usado esa clase para serializar los tipos en el código. De manera predeterminada, esta opción se establece en **Automático**, que especifica que los ensamblados de serialización se generan solo si ha usado <xref:System.Xml.Serialization.XmlSerializer> para codificar los tipos del código en XML. **Desactivado** especifica que los ensamblados de serialización no se generan nunca, independientemente de si el código usa <xref:System.Xml.Serialization.XmlSerializer>. **Activado** especifica que siempre se generan ensamblados de serialización. Los ensamblados de serialización se denominan `TypeName`.XmlSerializers.dll.  
  
## <a name="see-also"></a>Vea también  
 [Página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
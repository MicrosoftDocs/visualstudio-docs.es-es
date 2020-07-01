---
title: Configuración de compilador avanzada (Cuadro de diálogo, Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: ghogen
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0c0e6e9d41bb1d4bd7446bb77306ca5a4551906f
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419112"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>Configuración de compilador avanzada (Cuadro de diálogo, Visual Basic)

Use el cuadro de diálogo **Configuración de compilación avanzada** del **Diseñador de proyectos** para especificar las propiedades de configuración de compilación avanzada del proyecto. Este cuadro de diálogo solo se aplica a proyectos de Visual Basic.

## <a name="to-access-this-dialog-box"></a>Para obtener acceso a este cuadro de diálogo

1. En el **Explorador de soluciones**, elija el nodo de proyecto (no el nodo **Solución**).

2. En el menú **Proyecto**, haga clic en **Propiedades**. Cuando se muestre el **Diseñador de proyectos**, haga clic en la pestaña **Compilar**.

3. En la [página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md), seleccione **Configuración** y **Plataforma**. En las configuraciones de compilación simplificadas, no se muestran las listas **Configuración** y **Plataforma**. Para obtener más información, vea [Cómo: Establecer configuraciones Debug y Release](../../debugger/how-to-set-debug-and-release-configurations.md).

4. Haga clic en **Opciones de compilación avanzadas**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>Optimizaciones

Las opciones siguientes especifican optimizaciones que, en algunos casos, permiten reducir un archivo de programa, acelerar la ejecución de un programa o acelerar el proceso de compilación.

**Quitar comprobaciones de desbordamiento con enteros**

De manera predeterminada, esta casilla está desactivada para habilitar la comprobación de desbordamiento de enteros. Actívela para dejar de comprobar el desbordamiento con enteros. Si selecciona esta casilla, los cálculos de enteros pueden ser más rápidos. Sin embargo, si cancela la comprobación de desbordamiento y las capacidades de tipo de datos desbordan, puede ser que se almacenen resultados incorrectos sin que se emita ningún error.

Si se marcan las condiciones de desbordamiento y una operación de enteros desborda, se produce una excepción <xref:System.OverflowException>. Si las condiciones de desbordamiento no se comprueban, los desbordamientos de una operación de enteros no producen ninguna excepción.

**Habilitar optimizaciones**

De manera predeterminada, esta casilla está desactivada para deshabilitar las optimizaciones del compilador. Actívela para habilitar las optimizaciones del compilador. Gracias a las optimizaciones del compilador, el archivo de salida será más pequeño, más rápido y más eficaz. Sin embargo, puesto que las optimizaciones provocan una reorganización de código en el archivo de salida, las optimizaciones del compilador pueden dificultar la depuración.

 **Dirección base del archivo DLL**

En este cuadro de texto se muestra la dirección base predeterminada del archivo DLL en formato hexadecimal. En los proyectos de biblioteca de clases y biblioteca de controles, puede usar este cuadro de texto para especificar la dirección base que se usará al crear el archivo DLL.

 **Generar información de depuración**

Seleccione **Ninguna**, **Completa** o **Solo PDB** en la lista. **Ninguna** especifica que no se genera ninguna información de depuración. **Completa** especifica que se genera información de depuración completa y **Solo PDB** especifica que solo se debe generar información de depuración PDB. El valor predeterminado de esta opción es **Completa**.

## <a name="compilation-constants"></a>Constantes de compilación

Las constantes de compilación condicionales tienen un efecto parecido al de usar una directiva de preprocesador [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) en un archivo de origen, salvo por el hecho de que las constantes definidas son públicas y se aplican a todos los archivos del proyecto. Puede usar las constantes de compilación condicional junto con la directiva [#If...Then...#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) para compilar condicionalmente archivos de origen. Consulte [Compilación condicional](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).

 **Definir constante DEBUG**

De manera predeterminada, esta casilla está activada, lo que indica que se establece una constante DEBUG.

 **Definir constante TRACE**

De manera predeterminada, esta casilla está activada, lo que indica que se establece una constante TRACE.

 **Constantes personalizadas**

Escriba una de estas constantes personalizada para su aplicación en este cuadro de texto. Las entradas deben delimitarse mediante comas, con este formato: **Name1="Value1",Name2="Value2",Name3="Value3"** .

## <a name="other-settings"></a>Otras configuraciones

**Generar ensamblados de serialización**

Esta configuración especifica si el compilador creará ensamblados de serialización XML. Los ensamblados de serialización pueden mejorar el rendimiento de inicio de <xref:System.Xml.Serialization.XmlSerializer> si ha usado esa clase para serializar los tipos del código. El valor predeterminado de esta opción es **Automático**. **Automático** especifica que los ensamblados de serialización se generan solo si ha usado <xref:System.Xml.Serialization.XmlSerializer> para codificar los tipos del código en XML. **Desactivado** especifica que los ensamblados de serialización no se generan nunca, independientemente de si el código usa <xref:System.Xml.Serialization.XmlSerializer>. **Activado** especifica que siempre se generan ensamblados de serialización. Los ensamblados de serialización se denominan `TypeName`.XmlSerializers.dll.

## <a name="see-also"></a>Vea también

- [Página Compilación, Diseñador de proyectos (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)

---
title: "Configuraci&#243;n de compilador avanzada (Cuadro de di&#225;logo, Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesAdvancedCompile"
helpviewer_keywords: 
  - "Cuadro de diálogo Configuración de compilador avanzada"
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Configuraci&#243;n de compilador avanzada (Cuadro de di&#225;logo, Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo **Configuración de compilador avanzada** del **Diseñador de proyectos** se utiliza para especificar las propiedades de configuración de generación avanzada del proyecto.  Este cuadro de diálogo se aplica únicamente a los proyectos de Visual Basic.  
  
### Para obtener acceso a este cuadro de diálogo  
  
1.  En **Explorador de soluciones**, elija un nodo del proyecto \(no el nodo **Solución** \).  
  
2.  En el menú **Proyecto**, haga clic en **Propiedades**.  Cuando aparezca el **Diseñador de proyectos**, haga clic en la ficha **Compilar**.  
  
3.  En la [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md), seleccione **Configuración** y **Plataforma**.  En las configuraciones de compilación simplificada, las listas **Configuración** y **Plataforma** no se muestran.  Para obtener más información, vea [Debug and Release Project Configurations](http://msdn.microsoft.com/es-es/0440b300-0614-4511-901a-105b771b236e).  
  
4.  Haga clic en **Opciones de compilación avanzadas**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
## Optimizaciones  
 Las opciones siguientes especifican las optimizaciones que en algunos casos pueden reducir el tamaño del archivo de programa, hacer que el programa se ejecute más rápido o acelerar el proceso de compilación.  
  
 **Quitar comprobaciones de desbordamiento con enteros**  
 De forma predeterminada, esta casilla está desactivada para habilitar comprobar entero de desbordamiento.  Active esta casilla para quitar comprobar entero de desbordamiento.  Si activa esta casilla, los cálculos enteros pueden ser más rápidos.  Sin embargo, si quita el desbordamiento que comprueba y funciones desborda el tipo de datos, los resultados incorrectos se pueden almacenar sin un error que se produce.  
  
 Si se comprueban las condiciones de desbordamiento y los desbordamientos de una operación de entero, se produce una excepción de <xref:System.OverflowException>.  Si las condiciones de desbordamiento no se comprueban, desbordamientos enteros de la operación no producen una excepción.  
  
 **Habilitar optimizaciones**  
 De forma predeterminada, esta casilla está desactivada para deshabilitar las optimizaciones del compilador.  Actívela para habilitar las optimizaciones del compilador.  Las optimizaciones del compilador hacen que el archivo de salida sea más pequeño, rápido y eficaz.  Sin embargo, porque las optimizaciones hacen que el cambio de código en el archivo de salida, las optimizaciones del compilador pueden crear depurar difícil.  
  
 **Dirección base del archivo DLL**  
 Este cuadro de texto muestra la dirección base predeterminada del archivo DLL en formato hexadecimal.  En los proyectos de Biblioteca de clases y Biblioteca de controles, se puede utilizar para especificar la dirección base que se va a usar al crear el archivo DLL.  
  
 **Generar información de depuración**  
 Seleccione **Ninguno**, **Completo**, o **pdb únicamente** en la lista.  **Ninguno** especifica que no se genera información de depuración;  **Completo** que se genera la información de depuración completa, y **pdb únicamente** especifica que se genera únicamente información de depuración PDB.  De forma predeterminada, esta opción se establece en **Completo**.  
  
## Constantes de compilación  
 Las constantes de compilación condicional tienen un efecto similar al de una directiva de preprocesador de [\#Const](/dotnet/visual-basic/language-reference/directives/const-directive) en un archivo de código fuente, salvo que las constantes definidas son públicas y se aplican a todos los archivos del proyecto.  Puede utilizar constantes de compilación condicional junto con la directiva de [\#Else De Then \#If……](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) para compilar los archivos de código fuente condicional.  Vea [Compilación condicional](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation).  
  
 **Definir constante DEBUG**  
 De forma predeterminada, esta casilla está activada, especificando que se establece una constante DEBUG.  
  
 **Definir constante TRACE**  
 De forma predeterminada, esta casilla está activada, especificando que se establece una constante TRACE.  
  
 **Constantes personalizadas**  
 Escriba en este cuadro de texto una constante personalizada para su aplicación.  Las entradas deben estar delimitadas por comas, de la siguiente forma: Nombre1\="Valor1",Nombre2\="Valor2",Nombre3\="Valor3".  
  
## Otros valores  
 **Generar ensamblados de serialización**  
 Esta configuración especifica si el compilador creará ensamblados de serialización XML.  Los ensamblados de serialización pueden mejorar el rendimiento de inicio de <xref:System.Xml.Serialization.XmlSerializer> si se ha utilizado esa clase para serializar los tipos del código.  De forma predeterminada, esta opción se establece en **Automático**, que especifica que los ensamblados de serialización se generan sólo si ha utilizado <xref:System.Xml.Serialization.XmlSerializer> para codificar los tipos del código en XML.  **Desactivado** especifica que nunca se van a generar los ensamblados de serialización, sin tener en cuenta si el código utiliza <xref:System.Xml.Serialization.XmlSerializer>.  **Activado** especifica que siempre se generan los ensamblados de serialización.  Los ensamblados de serialización se denominan `TypeName`.XmlSerializers.dll.  
  
## Vea también  
 [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)
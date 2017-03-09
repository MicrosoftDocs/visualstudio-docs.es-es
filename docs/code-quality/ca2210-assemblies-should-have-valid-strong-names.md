---
title: "CA2210: Los ensamblados deben tener nombres seguros v&#225;lidos | Microsoft Docs"
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
  - "AssembliesShouldHaveValidStrongNames"
  - "CA2210"
helpviewer_keywords: 
  - "AssembliesShouldHaveValidStrongNames"
  - "CA2210"
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2210: Los ensamblados deben tener nombres seguros v&#225;lidos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AssembliesShouldHaveValidStrongNames|  
|Identificador de comprobación|CA2210|  
|Categoría|Microsoft.Design|  
|Cambio problemático|No|  
  
## Motivo  
 Un ensamblado no está firmado con un nombre seguro, el nombre seguro no puede comprobarse o no es válido sin la configuración de Registro actual del equipo.  
  
## Descripción de la regla  
 Esta regla recupera y comprueba el nombre seguro de un ensamblado.  Se produce una infracción si cualquiera de los siguientes condiciones es verdadera:  
  
-   El ensamblado no tiene un nombre seguro.  
  
-   El ensamblado se modificó después de la firma.  
  
-   El ensamblado tiene firma retardada.  
  
-   El ensamblado se firmó incorrectamente o la firma produjo un error.  
  
-   El ensamblado exige una configuración del Registro para pasar la comprobación.  Por ejemplo, la herramienta de nombre seguro \(Sn.exe\) se utilizó para pasar por alto la comprobación para el ensamblado.  
  
 El nombre seguro protege los clientes de cargar inconscientemente un ensamblado con el que se ha alterado.  Los ensamblados sin nombres seguros sólo deben implementarse en escenarios muy limitados.  Si se comparten o se distribuyen ensamblados que no están correctamente firmados, el ensamblado puede manipularse, el Common Language Runtime podría no cargar el ensamblado o el usuario podría deshabilitar la comprobación del equipo.  Un ensamblado sin nombre seguro tiene los inconvenientes siguientes:  
  
-   No se pueden comprobar sus orígenes.  
  
-   El Common Language Runtime no puede advertir a los usuarios si se ha modificado el contenido del ensamblado.  
  
-   No se puede cargar en la caché global de ensamblados.  
  
 Tenga en cuenta que cargar y analizar un ensamblado con firma retardada, debe deshabilitar la comprobación para el ensamblado.  
  
## Cómo corregir infracciones  
 **Para crear un archivo de clave**  
  
 Use uno de los procedimientos siguientes:  
  
-   Utilice la herramienta Vinculador de ensamblado \(Al.exe\) proporcionada por [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
-   Para [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] v1.0 o v1.1, utilice <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o el atributo <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>.  
  
-   Para [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], use la opción del compilador `/keyfile` o `/keycontainer` \(opción del vinculador [\/KEYFILE \(Especificar una clave o par de claves para firmar un ensamblado\)](/visual-cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) o [\/KEYCONTAINER \(Especificar un contenedor de claves para firmar un ensamblado\)](/visual-cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) en C\+\+\).  
  
 **Para firmar un ensamblado con un nombre seguro en Visual Studio**  
  
1.  En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], abra la solución.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en un proyecto y, a continuación, seleccione **Propiedades**.  
  
3.  Haga clic en la ficha **Firma** y active la casilla **Firmar el ensamblado**.  
  
4.  En **Elija un archivo de clave de nombre seguro**, seleccione **Nuevo**.  
  
     Aparece la ventana **Crear clave de nombre seguro**.  
  
5.  En **Nombre del archivo de clave**, escriba un nombre para la clave de nombre seguro.  
  
6.  Elija si desea proteger la clave con una contraseña y, a continuación, haga clic en **Aceptar**.  
  
7.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, seleccione **Compilar**.  
  
 **Para firmar un ensamblado con un nombre seguro fuera de Visual Studio**  
  
-   Utilice la herramienta de nombre seguro \(Sn.exe\) proporcionada por el SDK de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  Para obtener más información, vea [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md).  
  
## Cuándo suprimir advertencias  
 Sólo debe suprimir una advertencia de esta regla si el ensamblado se usa en un entorno donde la manipulación del contenido no es un problema.  
  
## Vea también  
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>   
 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>   
 [Cómo: Firmar un ensamblado con un nombre seguro](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)   
 [Sn.exe \(Strong Name Tool\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)
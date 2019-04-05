---
title: Usar los comprobadores de C++ Core Guidelines | Documentos de Microsoft
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: c0fb306cb7326464af847f09b319e8e702c76831
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998102"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usar los comprobadores de C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines son un conjunto de directrices, reglas y procedimientos recomendados sobre cómo codificar en C++ creados por los diseñadores y expertos de C++ portátil.  Visual Studio ahora admite paquetes de complementos que creación reglas adicionales para el código de las herramientas de análisis para comprobar el código para el cumplimiento de C++ Core Guidelines y sugerir mejoras.  
  
## <a name="the-c-core-guidelines-project"></a>El proyecto de C++ Core Guidelines  
 Creado por Bjarne Stroustrup etc., C++ Core Guidelines son una guía para utilizar C++ moderno de forma segura y eficaz. Hacer hincapié en las directrices de seguridad de tipos estáticos y seguridad de recursos. Se identifican formas de eliminar o minimizar las partes más propensos a errores del lenguaje y sugieren cómo hacer que el código sea más sencillo y más eficaces de forma confiable. Estas instrucciones se mantienen por la base de C++ estándar. Para obtener más información, consulte la documentación, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)y obtener acceso a los archivos de proyecto de la documentación de C++ Core Guidelines en [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft admite el esfuerzo de C++ Core Guidelines mediante la realización de C++ Core Check conjuntos de reglas de análisis de código que puede agregar a los proyectos mediante un paquete de Nuget. El paquete se denomina Microsoft.CppCoreCheck, y está disponible en [ http://www.nuget.org/packages/Microsoft.CppCoreCheck ](http://www.nuget.org/packages/Microsoft.CppCoreCheck). Este paquete requiere que tenga al menos Visual Studio 2015 con Update 1 instalado.  
  
 El paquete también instala otro paquete como una dependencia de un solo encabezado directriz soporte técnico de biblioteca (GSL). También está disponible en GitHub en el GSL [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar las instrucciones en el análisis de código de C++ Core Check  
 Para habilitar las herramientas de análisis de código de C++ Core Check, instale el paquete de Microsoft.CppCoreCheck NuGet en cada proyecto de C++ que se desea comprobar dentro de Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Para agregar el paquete de Microsoft.CppCoreCheck al proyecto  
  
1. En **el Explorador de soluciones**, con el botón secundario para abrir el menú contextual del proyecto en la solución que desea agregar el paquete. Elija **administrar paquetes de NuGet** para abrir el **Administrador de paquetes de NuGet**.  
  
2. En el **Administrador de paquetes de NuGet** ventana, busque Microsoft.CppCoreCheck.  
  
    ![Ventana Administrador de paquetes de NuGet muestra paquete CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Seleccione el paquete Microsoft.CppCoreCheck y, a continuación, elija el **instalar** para agregar las reglas a su proyecto.  
  
   El paquete NuGet agrega un archivo .targets de MSBuild adicional al proyecto que se invoca cuando se habilita el análisis de código en el proyecto. Este archivo .targets agrega las reglas de C++ Core Check como una extensión adicional a la herramienta de análisis de código de Visual Studio.  
  
   Puede habilitar el análisis de código en el proyecto seleccionando el **Habilitar análisis de código al compilar** casilla de verificación en la **análisis de código** sección de la **páginas de propiedades** cuadro de diálogo el proyecto.  
  
   ![Página de propiedades de configuración General de análisis de código](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Las reglas de C++ Core Check se convierten en parte de los conjuntos de reglas predeterminado que se ejecutan cuando se habilita el análisis de código. Dado que las reglas de C++ Core Check están en desarrollo, algunas reglas no pueden estar listos para su uso en todo el código, pero pueden ser informativas durante el desarrollo. Estas reglas se publican como experimental. Puede elegir si desea ejecutar las reglas publicadas o experimentales en las propiedades del proyecto.  
  
   ![Página de propiedades de configuración de extensiones de análisis de código](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Para habilitar o deshabilitar los conjuntos de reglas de C++ Core Check, abra el **páginas de propiedades** cuadro de diálogo para el proyecto. En **propiedades de configuración**, expanda **análisis de código**, **extensiones**. En la lista desplegable junto al control **habilitar C++ Core Check (lanzamiento)** o **habilitar C++ Core Check (Experimental)**, elija **Sí** o **No**. Elija **Aceptar** o **aplicar** para guardar los cambios.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Compruebe los tipos, límites y duraciones  
 El paquete de C++ Core Check contiene actualmente los comprobadores de la [seguridad de tipos](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [delimita seguridad](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds), y [seguridad duración](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) perfiles.  
  
 Este es un ejemplo del tipo de problemas que pueden encontrar las reglas de C++ Core Check:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 En este ejemplo muestra algunas de las advertencias que pueden encontrar las reglas de C++ Core Check:  
  
- C26494 es tipo.5 de regla: Siempre debe inicializarse un objeto.  
  
- C26485 es Bounds.3 de regla: No hay decadencia de matriz a puntero.  
  
- C26481 es Bounds.1 de regla: No usar aritmética de puntero. Utilice `span` en su lugar.  
  
  Si los rulesets de análisis de código de C++ Core Check estén instalados y habilitados cuando se compila este código, las dos primeras advertencias son de salida, pero se suprime la tercera. Este es el resultado de compilación del código de ejemplo:  
  
  **1 >---compilación iniciada: Proyecto: CoreCheckExample, configuración: Depurar Win32:**  
**----**  
**1 > CoreCheckExample.cpp**  
**1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1>  CoreCheckExample.vcxproj -> C:\Users\username\documents\visual studio 2015\P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (Full PDB)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(6): advertencia C26494: La variable 'arr' es uninitializ**  
**Ed. siempre debe inicializarse un objeto. (type.5: http://go.microsoft.com/fwlink/p/?Link**  
**ID. = 620421)**  
**c:\users\username\documents\visual studio 2015\projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp(7): advertencia C26485: Expresión 'arr': No hay matriz a**  
 **decadencia de puntero. (bounds.3: http://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**=== La compilación: 1 correctos, 0 incorrectos, 0 actualizados, 0 omitidos ===** The C++ Core Guidelines sirven para ayudarle a escribir código mejor y más seguro. Sin embargo, si tiene una instancia que no debe aplicarse una regla o un perfil, es fácil que la suprima directamente en el código. Puede usar el `gsl::suppress` atributo para impedir que C++ Core Check detectar e informes de cualquier infracción de una regla en el bloque de código siguiente. Puede marcar las instrucciones individuales para suprimir reglas específicas. Incluso puede suprimir todo el perfil bounds escribiendo `[[gsl::suppress(bounds)]]` sin necesidad de incluir un número específico de regla.  
  
## <a name="use-the-guideline-support-library"></a>Uso de la biblioteca de compatibilidad con criterio  
 El paquete Microsoft.CppCoreCheck NuGet también instala un paquete que contiene la implementación de Microsoft de la biblioteca de soporte técnico de directriz (GSL). También está disponible de forma independiente en el GSL [ http://www.nuget.org/packages/Microsoft.Gsl ](http://www.nuget.org/packages/Microsoft.Gsl). Esta biblioteca es útil si desea seguir las instrucciones de núcleo. El GSL incluye las definiciones que le permiten reemplazar construcciones propensas a errores por alternativas más seguras. Por ejemplo, puede reemplazar un `T*, length` par de parámetros con el `span<T>` tipo. El GSL es código abierto, por lo que si desea echar un vistazo a los orígenes de biblioteca, comentario o contribuir, puede encontrar el proyecto en [ https://github.com/Microsoft/GSL ](https://github.com/Microsoft/GSL).

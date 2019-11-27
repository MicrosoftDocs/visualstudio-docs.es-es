---
title: Usar los C++ comprobadores de directrices principales | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: ccc44b77c4524e7d707ce3fe407d204d729017ff
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291235"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usar los comprobadores de C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las C++ instrucciones básicas son un conjunto portátil de directrices, reglas y prácticas recomendadas sobre la codificación C++ en creadas C++ por expertos y diseñadores.  Visual Studio ahora admite paquetes de complementos que crean reglas adicionales para las herramientas de análisis de código con el fin de comprobar el C++ cumplimiento del código con las directrices básicas y sugerir mejoras.  
  
## <a name="the-c-core-guidelines-project"></a>Proyecto C++ de directrices básicas  
 Creado por Bjarne Stroustrup y otros, las C++ directrices principales son una guía para el uso C++ moderno y seguro de forma segura. Las instrucciones resaltan la seguridad de tipos estáticos y la seguridad de los recursos. Identifican maneras de eliminar o minimizar las partes más propensas a errores del lenguaje y sugieren cómo hacer que el código sea más sencillo y más eficaz de forma confiable. Estas instrucciones las mantiene la base estándar C++ . Para obtener más información, consulte la documentación, C++ [ C++ las directrices principales](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)y el acceso a los archivos de proyecto de documentación de directrices básicas en [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft admite el C++ esfuerzo de las directrices básicas C++ mediante el uso de conjuntos de reglas de análisis de código de comprobación básica que puede Agregar a los proyectos mediante un paquete Nuget. El paquete se denomina Microsoft. CppCoreCheck y está disponible en [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck). Este paquete requiere que haya al menos Visual Studio 2015 con Update 1 instalado.  
  
 El paquete también instala otro paquete como una dependencia, una biblioteca de compatibilidad de instrucciones solo de encabezado (GSL). GSL también está disponible en GitHub en [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar las C++ directrices de la comprobación básica en el análisis de código  
 Para habilitar las C++ herramientas de análisis de código de comprobación básica, instale el paquete NuGet Microsoft. C++ CppCoreCheck en cada proyecto que desee comprobar en Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Para agregar el paquete Microsoft. CppCoreCheck al proyecto  
  
1. En **Explorador de soluciones**, haga clic con el botón derecho para abrir el menú contextual del proyecto en la solución a la que desea agregar el paquete. Elija **administrar paquetes Nuget** para abrir el **Administrador de paquetes Nuget**.  
  
2. En la ventana **Administrador de paquetes NuGet** , busque Microsoft. CppCoreCheck.  
  
    ![La ventana Administrador de paquetes Nuget muestra el paquete CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Seleccione el paquete Microsoft. CppCoreCheck y, a continuación, elija el botón **instalar** para agregar las reglas al proyecto.  
  
   El paquete NuGet agrega un archivo MSBuild. targets adicional al proyecto que se invoca cuando se habilita el análisis de código en el proyecto. Este archivo. targets agrega C++ las reglas de comprobación básicas como extensión adicional a la herramienta de análisis de código de Visual Studio.  
  
   Puede habilitar el análisis de código en el proyecto activando la casilla **Habilitar análisis de código al compilar** en la sección **análisis de código** del cuadro de diálogo **páginas de propiedades** del proyecto.  
  
   ![Página de propiedades de la configuración general de análisis de código](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Las C++ reglas de comprobación básicas forman parte de los conjuntos de reglas predeterminados que se ejecutan cuando se habilita el análisis de código. Dado que C++ las reglas de comprobación básica están en desarrollo, algunas reglas pueden no estar listas para su uso en todo el código, pero pueden ser informativas durante el desarrollo. Estas reglas se publican como experimentales. Puede elegir si desea ejecutar las reglas publicadas o experimentales en las propiedades del proyecto.  
  
   ![Página de propiedades de la configuración de extensiones de análisis de código](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Para habilitar o deshabilitar C++ los conjuntos de reglas de comprobación básica, abra el cuadro de diálogo **páginas de propiedades** del proyecto. En **propiedades de configuración**, expanda **análisis de código**, **extensiones**. En el control desplegable situado **junto C++ a habilitar comprobación básica (lanzamiento)** o **habilitar C++ comprobación básica (experimental)** , elija **sí** o **no**. Elija **Aceptar** o **aplicar** para guardar los cambios.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Comprobar tipos, límites y duraciones  
 El C++ paquete de comprobación básica contiene actualmente los comprobadores de los perfiles [seguridad de tipos](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), seguridad de los [límites](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)y seguridad de la [duración](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Este es un ejemplo del tipo de problemas que pueden encontrar C++ las reglas de comprobación básicas:  
  
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
  
 En este ejemplo se muestran algunas de las advertencias que C++ las reglas de comprobación básicas pueden encontrar:  
  
- C26494 es el tipo de regla. 5: inicializar siempre un objeto.  
  
- C26485 es un límite de reglas. 3: no hay decadencia de matriz a puntero.  
  
- C26481 es un límite de regla. 1: no se usa aritmética de punteros. Utilice `span` en su lugar.  
  
  Si los C++ conjuntos de herramientas de análisis de código de comprobación básica se instalan y se habilitan al compilar este código, se generan las dos primeras advertencias, pero se suprime la tercera. Este es el resultado de la compilación del código de ejemplo:  
  
**1 >------compilación iniciada: proyecto: CoreCheckExample, configuración: depurar Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): ADVERTENCIA C26494: la variable ' ARR ' es uninitializ**  
**Ed. inicializar siempre un objeto. (tipo. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): ADVERTENCIA C26485: expresión ' ARR ': no hay matriz a**  
**caída del puntero. (Bounds. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
= = = = = = = = = **= Compilación: 1 correcta, 0 con errores, 0 actualizados, 0 omitidos = =** = = = = = = = = Aquí C++ encontrará instrucciones básicas que le ayudarán a escribir código mejor y más seguro. Sin embargo, si tiene una instancia de en la que no se debe aplicar una regla o un perfil, es fácil suprimirla directamente en el código. Puede usar el atributo `gsl::suppress` para mantener C++ la comprobación principal de detectar e informar de cualquier infracción de una regla en el siguiente bloque de código. Puede marcar instrucciones individuales para suprimir reglas específicas. Incluso puede suprimir el perfil de límite completo escribiendo `[[gsl::suppress(bounds)]]` sin incluir un número de regla específico.  
  
## <a name="use-the-guideline-support-library"></a>Usar la biblioteca de compatibilidad de directrices  
 El paquete NuGet Microsoft. CppCoreCheck también instala un paquete que contiene la implementación de Microsoft de la biblioteca de compatibilidad de instrucciones (GSL). GSL también está disponible en formato independiente en [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl). Esta biblioteca es útil si desea seguir las directrices básicas. GSL incluye definiciones que permiten reemplazar construcciones propensas a errores por alternativas más seguras. Por ejemplo, puede reemplazar un par `T*, length` de parámetros con el tipo `span<T>`. El GSL es de código abierto, por lo que si desea echar un vistazo a los orígenes de biblioteca, comentarios o contribuir, el proyecto se puede encontrar en [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL).

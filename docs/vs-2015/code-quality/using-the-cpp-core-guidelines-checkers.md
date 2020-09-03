---
title: Usar los comprobadores de C++ Core Guidelines | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173579"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Usar los comprobadores de C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los C++ Core Guidelines son un conjunto portátil de directrices, reglas y procedimientos recomendados sobre la codificación en C++ creados por expertos y diseñadores de C++.  Visual Studio ahora admite paquetes de complementos que crean reglas adicionales para las herramientas de análisis de código con el fin de comprobar el cumplimiento del código en el C++ Core Guidelines y sugerir mejoras.  
  
## <a name="the-c-core-guidelines-project"></a>Proyecto C++ Core Guidelines  
 Creado por Bjarne Stroustrup y otros, el C++ Core Guidelines es una guía para el uso de C++ moderno de forma segura y eficaz. Las instrucciones resaltan la seguridad de tipos estáticos y la seguridad de los recursos. Identifican maneras de eliminar o minimizar las partes más propensas a errores del lenguaje y sugieren cómo hacer que el código sea más sencillo y más eficaz de forma confiable. Estas instrucciones son mantenidas por la base de C++ estándar. Para más información, consulte la documentación, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)y acceda a los archivos de proyecto de documentación C++ Core Guidelines en [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Microsoft admite el C++ Core Guidelines esfuerzo al hacer C++ Core Check conjuntos de reglas de análisis de código que puede Agregar a los proyectos mediante un paquete Nuget. El paquete se denomina Microsoft. CppCoreCheck y está disponible en [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Este paquete requiere que haya al menos Visual Studio 2015 con Update 1 instalado.  
  
 El paquete también instala otro paquete como una dependencia, una biblioteca de compatibilidad de instrucciones solo de encabezado (GSL). GSL también está disponible en GitHub en [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Habilitar las directrices de C++ Core Check en el análisis de código  
 Para habilitar las herramientas de análisis de código C++ Core Check, instale el paquete NuGet Microsoft. CppCoreCheck en cada proyecto de C++ que quiera comprobar en Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Para agregar el paquete Microsoft. CppCoreCheck al proyecto  
  
1. En **Explorador de soluciones**, haga clic con el botón derecho para abrir el menú contextual del proyecto en la solución a la que desea agregar el paquete. Elija **administrar paquetes Nuget** para abrir el **Administrador de paquetes Nuget**.  
  
2. En la ventana **Administrador de paquetes NuGet** , busque Microsoft. CppCoreCheck.  
  
    ![La ventana Administrador de paquetes Nuget muestra el paquete CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Seleccione el paquete Microsoft. CppCoreCheck y, a continuación, elija el botón **instalar** para agregar las reglas al proyecto.  
  
   El paquete NuGet agrega un archivo MSBuild. targets adicional al proyecto que se invoca cuando se habilita el análisis de código en el proyecto. Este archivo. targets agrega las reglas de C++ Core Check como extensión adicional a la herramienta de análisis de código de Visual Studio.  
  
   Puede habilitar el análisis de código en el proyecto activando la casilla **Habilitar análisis de código al compilar** en la sección **análisis de código** del cuadro de diálogo **páginas de propiedades** del proyecto.  
  
   ![Página de propiedades de la configuración general de análisis de código](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Las reglas de C++ Core Check forman parte de los conjuntos de reglas predeterminados que se ejecutan cuando se habilita el análisis de código. Dado que las reglas de C++ Core Check están en desarrollo, algunas reglas pueden no estar listas para su uso en todo el código, pero pueden ser informativas durante el desarrollo. Estas reglas se publican como experimentales. Puede elegir si desea ejecutar las reglas publicadas o experimentales en las propiedades del proyecto.  
  
   ![Página de propiedades de la configuración de extensiones de análisis de código](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Para habilitar o deshabilitar los conjuntos de reglas de C++ Core Check, abra el cuadro de diálogo **páginas de propiedades** del proyecto. En **propiedades de configuración**, expanda  **análisis de código**, **extensiones**. En el control desplegable situado junto a **habilitar C++ Core check (lanzamiento)** o **Habilitar C++ Core check (experimental)**, elija **sí** o **no**. Elija **Aceptar** o **aplicar** para guardar los cambios.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Comprobar tipos, límites y duraciones  
 El paquete de C++ Core Check contiene actualmente los comprobadores de los perfiles [seguridad de tipos](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), seguridad de los [límites](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)y [seguridad de duración](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
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
  
 En este ejemplo se muestran algunas de las advertencias que las reglas de C++ Core Check pueden encontrar:  
  
- C26494 es el tipo de regla. 5: inicializar siempre un objeto.  
  
- C26485 es un límite de reglas. 3: no hay decadencia de matriz a puntero.  
  
- C26481 es un límite de regla. 1: no se usa aritmética de punteros. Utilice `span` en su lugar.  
  
  Si el C++ Core Check conjuntos de herramientas de análisis de código se instalan y se habilitan al compilar este código, se generan las dos primeras advertencias, pero se suprime la tercera. Este es el resultado de la compilación del código de ejemplo:  
  
**1>------compilación iniciada: proyecto: CoreCheckExample, configuración: depurar Win32--**  
**----**  
**1> CoreCheckExample. cpp**  
**1> CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> CoreCheckExample. vcxproj-> C:\Users\username\documents\visual Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (PDB completo)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (6): ADVERTENCIA C26494: la variable ' ARR ' es uninitializ**  
**Ed. Inicialice siempre un objeto. (tipo. 5: https: \/ /Go.Microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\documents\visual Studio 2015 \ projects\corecheckexample\coreche**  
**ckexample\corecheckexample.cpp (7): ADVERTENCIA C26485: expresión ' ARR ': no hay matriz a**  
**caída del puntero. (Bounds. 3: https: \/ /Go.Microsoft.com/fwlink/p/?LinkId=620415)**  
**========== Compilación: 1 correctos, 0 incorrectos, 0 actualizados, 0 omitidos ==========** 

El C++ Core Guidelines está ahí para ayudarle a escribir código mejor y más seguro. Sin embargo, si tiene una instancia de en la que no se debe aplicar una regla o un perfil, es fácil suprimirla directamente en el código. Puede usar el `gsl::suppress` atributo para evitar que C++ Core check detecten y notifiquen cualquier infracción de una regla en el siguiente bloque de código. Puede marcar instrucciones individuales para suprimir reglas específicas. Incluso puede suprimir el perfil de límite completo escribiendo `[[gsl::suppress(bounds)]]` sin incluir un número de regla específico.  
  
## <a name="use-the-guideline-support-library"></a>Usar la biblioteca de compatibilidad de directrices  
 El paquete NuGet Microsoft. CppCoreCheck también instala un paquete que contiene la implementación de Microsoft de la biblioteca de compatibilidad de instrucciones (GSL). GSL también está disponible en formato independiente en [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Esta biblioteca es útil si desea seguir las directrices básicas. GSL incluye definiciones que permiten reemplazar construcciones propensas a errores por alternativas más seguras. Por ejemplo, puede reemplazar un `T*, length` par de parámetros con el `span<T>` tipo. El GSL es de código abierto, por lo que si desea echar un vistazo a los orígenes de biblioteca, comentarios o contribuir, el proyecto se puede encontrar en [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .

---
title: "Valores de m&#233;trica de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "métrica de código"
  - "análisis de código"
  - "medir la calidad del código"
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 20
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 20
---
# Valores de m&#233;trica de c&#243;digo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las métricas de código son un conjunto de medidas de software que proporcionan a los programadores una mejor visión del código que están desarrollando.  Al aprovechar las métricas de código, los programadores pueden entender qué tipos y métodos se deben rehacer o probar más a fondo.  Los equipos de desarrollo pueden identificar los riesgos potenciales, entender el estado actual de un proyecto y seguir el progreso durante el desarrollo del software.  
  
## Medidas del software  
 En la lista siguiente se muestran los resultados de las métricas de código que calcula [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   **Índice de mantenimiento**: calcula un valor de índice entre 0 y 100 que representa la facilidad relativa de mantenimiento del código.  Un valor alto significa mayor facilidad de mantenimiento.  Las calificaciones codificadas por colores se pueden utilizar para identificar rápidamente puntos problemáticos del código.  Una clasificación verde se encuentra entre 20 y 100 e indica que el mantenimiento del código es bueno.  Una clasificación amarilla se encuentra entre 10 y 19 e indica que el mantenimiento del código es moderado.  Una clasificación roja se encuentra entre 0 y 9 e indica un mantenimiento pobre.  
  
-   **Complejidad ciclomática**: mide la complejidad estructural del código.  Se crea calculando el número de rutas de acceso del código diferentes del flujo del programa.  Un programa que tenga un flujo de control complejo requerirá más pruebas para lograr una buena cobertura de código y será más difícil de mantener.  
  
    > [!NOTE]
    >  En algunos casos, el cálculo de la complejidad ciclomática de un método de [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] difiere de las versiones anteriores.  Para obtener más información, vea la sección "Cambios en cálculos de complejidad de código de Visual Studio 2010" de [Solucionar problemas de métricas de código](../code-quality/troubleshooting-code-metrics-issues.md).  
  
-   **Profundidad de herencia**: indica el número de definiciones de clase que se extienden a la raíz de la jerarquía de clases.  Cuanto más profunda es la jerarquía, más difícil puede ser entender dónde se definen y se vuelven a definir determinados métodos y campos.  
  
-   **Acoplamiento de clases**: mide el acoplamiento a las clases únicas a través de parámetros, variables locales, tipos de valores devueltos, llamadas a métodos, instancias genéricas o de plantillas, clases base, implementaciones de interfaces, campos definidos en tipos externos y decoración de atributos.  El buen diseño de software sugiere que los tipos y métodos deben tener cohesión alta y acoplamiento bajo.  Un acoplamiento alto indica un diseño difícil de reutilizar y mantener debido a sus interdependencias en otros tipos.  
  
-   **Líneas de código**: indica el número aproximado de líneas del código.  El recuento se basa en el código IL y, por consiguiente, no representa el número exacto de líneas en el archivo de código fuente.  Un recuento muy alto podría indicar que un tipo o método intenta hacer demasiado trabajo y debe dividirse.  También puede indicar que el tipo o método podría ser difícil de mantener.  
  
## Métodos anónimos  
 Un *método anónimo* es simplemente un método que no tiene ningún nombre.  Los métodos anónimos se utilizan con más frecuencia para pasar un bloque de código como parámetro delegado.  Los resultados de las métricas para un método anónimo declarado en un miembro, ya sea como método o como descriptor de acceso, se asocian al miembro que declara el método.  No se asocian con el miembro que llama al método.  
  
 Para obtener más información sobre cómo tratan las métricas de código a los métodos anónimos, vea [Métodos anónimos y análisis de código](../code-quality/anonymous-methods-and-code-analysis.md).  
  
## Código generado  
 Algunas herramientas de software y compiladores generan código que se agrega a un proyecto y que el programador del proyecto no ve o no debe cambiar.  Principalmente, las métricas de código omiten el código generado cuando calculan los valores de métricas.  Esto permite que los valores de métricas reflejen lo que el programador puede ver y cambiar.  
  
 No se omite el código generado para formularios Windows Forms, porque es código que el programador puede ver y cambiar.  
  
## Vea también  
 [Medir la complejidad y el mantenimiento del código administrado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
---
title: advertencias de rendimiento
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305659"
---
# <a name="performance-warnings"></a>advertencias de rendimiento
Las advertencias de rendimiento admiten aplicaciones y bibliotecas de alto rendimiento.

## <a name="in-this-section"></a>En esta sección

| Regla | Descripción |
| - | - |
| [CA1800: No convertir innecesariamente @ no__t-0 | Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas. |
| [CA1801: Revisar los parámetros no usados @ no__t-0 | Una firma de método incluye un parámetro que no se utiliza en el cuerpo del método. |
| [CA1802: Usar literales donde corresponda @ no__t-0 | Un campo se declara estático y de solo lectura (Shared y ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) y se inicializa con un valor que se calcula en tiempo de compilación. Dado que el valor que se asigna al campo de destino se calcula en tiempo de compilación, cambie la declaración a const (Const en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) de campo para que el valor se calcula en tiempo de compilación en lugar de en tiempo de ejecución. |
| [CA1804: Quitar variables locales no usadas @ no__t-0 | Las variables locales no usadas y las asignaciones innecesarias aumentan el tamaño de un ensamblado y reducen el rendimiento. |
| [CA1806: No pasar por alto los resultados del método @ no__t-0 | Se crea un nuevo objeto, pero nunca se utiliza, o se llama a un método que crea y devuelve una nueva cadena y la nueva cadena nunca se utiliza, o un modelo de objetos componentes (COM) o un método P/Invoke devuelve un código de error o HRESULT que nunca se usa. |
| [CA1809: Evitar variables locales excesivas @ no__t-0 | Una optimización de rendimiento común es almacenar un valor en un registro del procesador en lugar de en la memoria, lo que se denomina "registrar el valor".  Para aumentar la probabilidad de que todas las variables locales son registren, limite el número de variables locales a 64. |
| [CA1810: Inicializar campos estáticos de tipo de referencia insertados @ no__t-0 | Cuando un tipo declara un constructor estático explícito, el compilador Just-In-Time (JIT) agrega una comprobación a cada constructor de instancia y a cada método estático del tipo para asegurarse de que se ha llamado anteriormente al constructor estático. Las comprobaciones del constructor estático pueden reducir el rendimiento. |
| [CA1811: Evitar el código privado no llamado @ no__t-0 | Un miembro privado o interno (nivel de ensamblado) no tiene llamadores en el ensamblado, no lo invoca el Common Language Runtime y no lo invoca un delegado. |
| [CA1812: Evite la creación de instancias de clases internas @ no__t-0 | El código del ensamblado no crea una instancia del tipo del nivel de ensamblado. |
| [CA1813: Evitar atributos no sellados @ no__t-0 | .NET proporciona métodos para recuperar atributos personalizados. De forma predeterminada, estos métodos buscan la jerarquía de herencia de atributo. La acción de sellar el atributo elimina la búsqueda en la jerarquía de herencia y puede mejorarse el rendimiento. |
| [CA1814: Preferir matrices escalonadas sobre @ no__t-0 multidimensional | Una matriz escalonada es una matriz cuyos elementos son matrices. Las matrices que componen los elementos pueden tener distintos tamaños, lo que puede dar lugar a menos espacio desperdiciado para algunos conjuntos de datos. |
| [CA1815: Invalidar Equals y el operador Equals en los tipos de valores](../code-quality/ca1815.md) | Para los tipos de valor, la implementación heredada de Equals utiliza la biblioteca de reflexión y compara el contenido de todos los campos. Mediante el cálculo, la reflexión es cara y no es necesario comparar cada campo para comprobar si hay igualdad. Si espera que los usuarios comparen u ordenen instancias, o utilicen instancias como claves de tabla hash, el tipo de valor debe implementar Equals. |
| [CA1816: Llame a GC. SuppressFinalize correctamente @ no__t-0 | Un método que es una implementación de Dispose no llama a GC. SuppressFinalize, o un método que no sea una implementación de Dispose llama a GC. SuppressFinalize, o un método llama a GC. SuppressFinalize y pasa algo distinto de This (me en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Las propiedades no deben devolver matrices @ no__t-0 | Las matrices devueltas por propiedades no están protegidas contra escritura, aunque la propiedad sea de solo lectura. Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz. Por lo general, los usuarios no entienden las implicaciones de rendimiento adversas que se originan al llamar a este tipo de propiedad. |
| [CA1820: Prueba de cadenas vacías mediante la longitud de cadena @ no__t-0 | El uso de la propiedad String.Length o del método String.IsNullOrEmpty para comparar cadenas es mucho más rápido que el uso de Equals. |
| [CA1821: quitar los finalizadores vacíos](../code-quality/ca1821.md) | Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto. Un finalizador vacío supone una sobrecarga adicional sin ninguna ventaja. |
| [CA1822: Marcar miembros como static @ no__t-0 | Los miembros que no tienen acceso a datos de instancia o que llaman a métodos de instancia se pueden marcar como static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Después de marcar los métodos como static, el compilador emite los sitios de llamada no virtuales para estos miembros. Esto puede proporcionar una mejora apreciable del rendimiento del código en el que el rendimiento es fundamental. |
| [CA1823: Evitar los campos privados no usados @ no__t-0 | Se detectaron campos privados a los que no parece que se tenga acceso en el ensamblado. |
| [CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute @ no__t-0 | El atributo NeutralResourcesLanguage informa a ResourceManager del idioma utilizado para mostrar los recursos de la referencia cultural neutral de un ensamblado. Esto mejora el rendimiento de la búsqueda del primer recurso que se carga y puede reducir el espacio de trabajo. |
| @NO__T 0CA1825: Evitar asignaciones de matrices de longitud cero @ no__t-0 | Al inicializar una matriz de longitud cero, se produce una asignación de memoria innecesaria. En su lugar, use la instancia de matriz vacía asignada estáticamente llamando a <xref:System.Array.Empty%2A?displayProperty=nameWithType>. La asignación de memoria se comparte entre todas las invocaciones de este método. |

---
title: CA5351 no usan algoritmos criptográficos rotos | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ad4698fe469176ae8ed590c44b4efbb4ccf39de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545059"
---
# <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351 No use algoritmos criptográficos rotos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotUseBrokenCryptographicAlgorithms|
|Identificador de comprobación|CA5351|
|Category|Microsoft.Cryptography|
|Cambio problemático|No trascendental|

> [!NOTE]
> Esta advertencia se actualizó por última vez en noviembre de 2015.

## <a name="cause"></a>Causa
 Las funciones hash como <xref:System.Security.Cryptography.MD5> y los algoritmos de cifrado como <xref:System.Security.Cryptography.DES> y <xref:System.Security.Cryptography.RC2> pueden generar riesgos significativos y provocar la divulgación de información confidencial a través de técnicas de ataque fáciles, como colisiones hash y ataques por fuerza bruta.

 La lista de algoritmos criptográficos siguiente está sujeta a ataques criptográficos conocidos. El algoritmo hash criptográfico <xref:System.Security.Cryptography.MD5> está sujeto a ataques de colisión hash.  En función del uso, una colisión hash puede provocar la suplantación, manipulación u otros tipos de ataques en sistemas que se basan en la salida criptográfica única de una función hash. Los algoritmos de cifrado <xref:System.Security.Cryptography.DES> y <xref:System.Security.Cryptography.RC2> están sujetos a ataques criptográficos que pueden provocar la divulgación no intencionada de datos cifrados.

## <a name="rule-description"></a>Descripción de la regla
 Los algoritmos criptográficos rotos no se consideran seguros y debe desalentarse su uso. El algoritmo hash MD5 es susceptible a ataques de colisión conocidos, aunque la vulnerabilidad específica variará según el contexto de uso.  Los algoritmos hash usados para garantizar la integridad de los datos (por ejemplo, signatura de archivo o certificado digital) son especialmente vulnerables.  En este contexto, los atacantes pueden generar dos fragmentos de datos separados, de tal manera que los datos correctos se pueden sustituir por los datos malintencionados, sin cambiar el valor hash ni invalidar una signatura digital asociada.

 Para algoritmos de cifrado:

- El cifrado<xref:System.Security.Cryptography.DES> contiene un pequeño tamaño de clave, que podría forzarse en menos de un día.

- El cifrado<xref:System.Security.Cryptography.RC2> es susceptible de sufrir ataques relacionados con la clave, en los que el atacante busca relaciones matemáticas entre todos los valores de clave.

  Esta regla se desencadena cuando se encuentra cualquiera de las funciones criptográficas anteriores en el código fuente y emite una advertencia al usuario.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Use opciones de criptografía más segura:

- Para MD5, use valores hash en la familia [Sha-2](https://msdn.microsoft.com/library/windows/desktop/aa382459.aspx) (por ejemplo <xref:System.Security.Cryptography.SHA512> ,, <xref:System.Security.Cryptography.SHA384> , <xref:System.Security.Cryptography.SHA256> ).

- Para DES y RC2, use el cifrado <xref:System.Security.Cryptography.Aes> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla a menos que la haya revisado un experto criptográfico.

## <a name="pseudo-code-example"></a>Ejemplo de pseudocódigo
 El ejemplo de pseudocódigo siguiente muestra el patrón que esta regla detecta y las alternativas posibles.

### <a name="md5-hashing-violation"></a>Infracción de hash MD5

```
using System.Security.Cryptography;
...
var hashAlg = MD5.Create();

```

### <a name="solution"></a>Solución

```
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();

```

### <a name="rc2-encryption-violation"></a>Infracción de cifrado RC2

```
using System.Security.Cryptography;
...
RC2 encAlg = RC2.Create();

```

### <a name="solution"></a>Solución

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```

### <a name="des-br-br-encryption-violation"></a>DES <br /><br />Infracción de cifrado

```
using System.Security.Cryptography;
...
DES encAlg = DES.Create();

```

### <a name="solution"></a>Solución

```
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```
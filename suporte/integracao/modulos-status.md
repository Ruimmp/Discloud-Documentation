---
description: Módulo para ler métricas do cgroup de contêineres modernos Linux
---

# Módulos Status

![](../../.gitbook/assets/image%20%2825%29%20%281%29%20%281%29.png)

## Informações

O limite de memória definidos nos contêiners é imposto via cgroups, e a maioria das ferramentas Linux que fornecem métricas de recursos do sistema foram criadas antes mesmo da existência de cgroups \(por exemplo: free ou top\).

Eles costumam ler métricas de memória do procsistema de arquivos: `/proc/meminfo`, `/proc/vmstat`, `/proc/PID/smaps` e outros. Isso significa que eles não têm consciência de cgroup . Eles sempre exibirão os números de memória do sistema host \(máquina física ou virtual\) como um todo, que é inútil para os contêineres modernos do Linux.

Esse módulo Nodejs funciona apenas no linux, e foi criado exclusivamente para atender os usuários da [discloudbot.com](https://discloud.com/)

As informações fornecidas pelo modulo são geradas pelo [cgroups](https://www.kernel.org/doc/Documentation/cgroup-v1/) no caminho `/sys/fs/cgroup/`

{% tabs %}
{% tab title="📦Javascript" %}
### Instalação do módulo

```bash
$ npm install discloud-status
```

### Forma de uso no JS

```javascript
const discloud = require("discloud-status");

// retorna o uso/total de RAM
let r = discloud.ram();
console.log(r) // 100/1024MB

// dados do uso de RAM
let ur = discloud.usoRam();
console.log(ur) // 100MB

// dados do total de RAM disponível
let tr = discloud.totalRam();
console.log(tr) //1GB
```

[https://www.npmjs.com/package/discloud-status](https://www.npmjs.com/package/discloud-status)
{% endtab %}

{% tab title="🐍Python" %}
### Instalação do módulo

```bash
$ pip install discloud
```

## Forma de uso no Python

```python
import discloud

# retorna o uso/total de RAM
r = discloud.ram()
print(r) # 100/1024MB

# dados do uso de RAM
ur = discloud.using_ram()
print(ur) # 100MB

# dados do total de RAM disponível
tr = discloud.total_ram()
print(tr) # 1GB
```

[https://pypi.org/project/discloud/](https://pypi.org/project/discloud/)
{% endtab %}

{% tab title="☕Java" %}
```text
package util;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.text.CharacterIterator;
import java.text.StringCharacterIterator;


public class discloudStatus {


	public static String convertMB(long bytes) {
		/**
	     *  convert kb to mb/gb/tb/...
	     */
	    long absB = bytes == Long.MIN_VALUE ? Long.MAX_VALUE : Math.abs(bytes);
	    if (absB < 1024) {
	        return bytes + " B";
	    }
	    long value = absB;
	    CharacterIterator ci = new StringCharacterIterator("KMGTPE");
	    for (int i = 40; i >= 0 && absB > 0xfffccccccccccccL >> i; i -= 10) {
	        value >>= 10;
	        ci.next();
	    }
	    value *= Long.signum(bytes);
	    return String.format("%.1f %ciB", value / 1024.0, ci.current());
	}

	public static File file_total(){
		/**
	     * convert localization to file
	     * (/sys/fs/cgroup/memory/memory.max_usage_in_bytes)
	     */
		return new File(File.separator+"sys"+File.separator+"fs"+File.separator+"cgroup"+File.separator+"memory"+File.separator+"memory.limit_in_bytes");
	}

	public static File file_used() {
		/**
	     * convert localization to file
	     * (/sys/fs/cgroup/memory/memory.limit_in_bytes)
	     */
		return new File(File.separator+"sys"+File.separator+"fs"+File.separator+"cgroup"+File.separator+"memory"+File.separator+"memory.max_usage_in_bytes");
	}

	@SuppressWarnings("resource")
	public static int total_ram() throws NumberFormatException, FileNotFoundException, IOException {
		/**
	     * get total space memory ram
	     */
		return Integer.parseInt(new BufferedReader(new FileReader(file_total())).readLine());
	}

	@SuppressWarnings("resource")
	public static int total_used() throws NumberFormatException, FileNotFoundException, IOException {
		/**
	     * get total memory used
	     */
		return Integer.parseInt(new BufferedReader(new FileReader(file_used())).readLine());
	}




	public static String ram() throws NumberFormatException, FileNotFoundException, IOException {
		/**
	     *  get memory ram converted to MB!
	     *  return (memoryused/memorytotal)
	     */
		return "("+convertMB(total_used())+"/"+convertMB(total_ram())+")";
	}
}
```
{% endtab %}
{% endtabs %}




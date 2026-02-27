| **Comando Redis**              | **Breve explicación**                                                 | **Ejemplo de salida**                                                        |
| ------------------------------ | --------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `PING`                         | Comprueba que el servidor Redis está vivo. Responde con un *PONG*.    | `127.0.0.1:6379> PING <br> PONG`                                             |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `SET clave valor`              | Guarda un par clave–valor en Redis.                                   | `127.0.0.1:6379> SET aitor-bd "url" <br> OK`                                 |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `GET clave`                    | Recupera el valor de una clave.                                       | `127.0.0.1:6379> GET aitor-bd <br> "aitor-medrano.github.io/bd"`             |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `MSET k1 v1 k2 v2 ...`         | Inserta múltiples pares clave–valor.                                  | `127.0.0.1:6379> MSET a b x y <br> OK`                                       |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `MGET k1 k2 ...`               | Recupera varios valores a la vez.                                     | `127.0.0.1:6379> MGET a b <br> 1) "v1" <br> 2) "v2"`                         |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `KEYS patrón`                  | Muestra todas las claves coincidentes (no recomendado en producción). | `127.0.0.1:6379> KEYS aitor-* <br> 1) "aitor-bd"`                            |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `SCAN cursor MATCH patrón`     | Itera claves sin bloquear el servidor (alternativa a KEYS).           | `127.0.0.1:6379> SCAN 0 MATCH usuario:* <br> 1) "0" <br> 2) (array of keys)` |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `DELETE` / `DEL clave`         | Elimina una clave y su valor.                                         | `127.0.0.1:6379> DEL aitor-bd <br> (integer) 1`                              |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `EXPIRE clave segundos`        | Establece tiempo a vivir (TTL) para una clave.                        | `127.0.0.1:6379> EXPIRE a 3600 <br> (integer) 1`                             |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `TTL clave`                    | Muestra tiempo restante hasta la expiración.                          | `127.0.0.1:6379> TTL a <br> (integer) 3283`                                  |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `INCR clave`                   | Incrementa un valor entero (útil para contadores).                    | `127.0.0.1:6379> INCR contador <br> (integer) 3`                             |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `MULTI` / `EXEC`               | Comienza y confirma una transacción (atomicidad).                     | `127.0.0.1:6379> MULTI <br> OK <br> ... <br> EXEC <br> 1) OK ...`            |
| ([aitor-medrano.github.io][1]) |                                                                       |                                                                              |
| `SAVE`                         | Fuerza un guardado de snapshot RDB en disco de forma **bloqueante**.  | `127.0.0.1:6379> SAVE <br> OK` (bloquea) ([LabEx][2])                        |
| `BGSAVE`                       | Inicia snapshot RDB en segundo plano (no bloquea).                    | `127.0.0.1:6379> BGSAVE <br> Background saving started`                      |
| ([LabEx][2])                   |                                                                       |                                                                              |
| `LASTSAVE`                     | Muestra el timestamp del último guardado RDB.                         | `127.0.0.1:6379> LASTSAVE <br> 1696802400` (Unix timestamp) ([LabEx][2])     |
| `CONFIG GET parámetro`         | Recupera valores de configuración del servidor Redis.                 | `127.0.0.1:6379> CONFIG GET dir <br> 1) "dir" <br> 2) "/data"`               |
| ([LabEx][2])                   |                                                                       |                                                                              |
| `CONFIG SET parámetro valor`   | Cambia configuración en caliente (temporal hasta reinicio).           | `127.0.0.1:6379> CONFIG SET appendonly yes <br> OK`                          |
| ([LabEx][2])                   |                                                                       |                                                                              |

[1]: https://aitor-medrano.github.io/bd/12redis.html "Redis - una base de datos clave-valor - Bases de datos"
[2]: https://labex.io/es/tutorials/redis-persistence-and-simple-configuration-in-redis-552079?utm_source=chatgpt.com "Persistencia y Configuración Sencilla en Redis | LabEx"

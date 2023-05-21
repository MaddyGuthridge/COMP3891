What happens if there are conflicting writes between [[CPU cache|caches]]? This could lead to memory corruption.

Dedicated cache consistency hardware is used to propagate changes or invalidate changed entries on other caches. However, cache transactions also consume [[bus-based uniform memory access|bus]] bandwidth.
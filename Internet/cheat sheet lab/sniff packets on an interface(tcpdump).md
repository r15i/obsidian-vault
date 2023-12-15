## Sniff Packets on an Interface

```bash
tcpdump -i <INTERFACE> -w <PATH_TO_PCAP_FILE>
```

### Example:
- Sniffing all data on the `eth0` interface and writing them to `/shared/test.pcap`:
  ```bash
  tcpdump -i eth0 -w /shared/test.pcap
  ```

This command captures network packets on the specified interface (`<INTERFACE>`) and saves them into a specified PCAP file (`<PATH_TO_PCAP_FILE>`).

### Note: Background Tcpdump

It's not ideal to run `tcpdump` in the background since halting it or saving data might not be straightforward.

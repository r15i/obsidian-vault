### Filter Table
usage: **contains basic packet filtering**
**chains**:
- INPUT
- OUTPUT
- FORWARD

**rules**:
- **ACCEPT** accept the packet 
- **DROP** silently discard it 
- **REJECT** discard and send an error to the source
- **user-defined-chain** redirects it to a specifed user-defined chain
- **RETURN** returns from the user-defined chain
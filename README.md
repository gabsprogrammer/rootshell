# rootshell

A free, Metal-accelerated terminal emulator for iPhone, iPad, Vision Pro, and Mac.

**[Website](https://beta.rootshell.com)** · **[TestFlight Beta](https://testflight.apple.com/join/DEVnH3N2)** · **[macOS Download](https://beta.rootshell.com/downloads/rootshell-macos-latest.tar.xz)**

## About

rootshell is a terminal emulator built for Apple platforms. It features GPU-accelerated rendering powered by libghostty, native SSH with jump host support, Secure Enclave key storage, cloud provider integration (AWS, Azure, Linode, DigitalOcean), Kubernetes node debugging, and Rootshell Roam — a mosh-compatible and tssh (QUIC+KCP) mobile terminal protocol with seamless network roaming and session persistence.

For full feature details, screenshots, and documentation, visit **[beta.rootshell.com](https://beta.rootshell.com)**.

## This Repository

This repository serves as the **public issue tracker** for rootshell. Use it to:

- Report bugs
- Request features
- Ask questions about functionality

## Reporting Issues

Before opening an issue, please:

1. **Check existing issues** to avoid duplicates
2. **Update to the latest version** via TestFlight or the macOS download
3. **Include relevant details** when reporting bugs:
   - App version (Settings → About)
   - Device and OS version
   - Steps to reproduce
   - Expected vs actual behavior
   - Any error messages or screenshots

### Issue Templates

- **Bug Report** - Something isn't working correctly
- **Feature Request** - Suggest a new feature or improvement
- **Question** - General questions about usage

## Getting the App

rootshell is **completely free** with no ads, subscriptions, or in-app purchases.

| Platform | Link |
|----------|------|
| iOS, iPadOS, visionOS, macOS (sandboxed) | [TestFlight](https://testflight.apple.com/join/DEVnH3N2) |
| macOS (standalone) | [Direct Download](https://beta.rootshell.com/downloads/rootshell-macos-latest.tar.xz) |

## Key Features

### Terminal & Rendering
- **Metal Accelerated** - GPU-accelerated rendering powered by [libghostty](https://github.com/ghostty-org/ghostty) with buttery smooth scrolling
- **450+ Themes** - Curated color themes with live preview, favorites, and per-tab overrides
- **Day/Night Themes** - Automatic theme switching based on sunrise/sunset at your location
- **Tabs & Splits** - Resizable split windows within tabs with session persistence
- **Session Restoration** - Tabs, splits, themes, and connections restore automatically on launch
- **Nerd Fonts** - Multiple monospace Nerd Fonts built-in with full icon support

### Visual Effects
- **Custom Shaders** - Import shaders directly from Shadertoy with full uniform support
- **Cursor Effects** - Warp, Sweep, Tail, and Blaze cursor animations
- **Background Effects** - Solar (real-time sun tracking), Starfield, Fireflies, Aurora, Nebula
- **Video Backgrounds** - Play looping video files as terminal backgrounds with speed control
- **Window Transparency** - Configurable transparency with blur (macOS)

### SSH & Networking
- **Native SSH Client** - Written entirely in Swift with no external dependencies
- **Jump Hosts** - Multi-hop connections through bastion servers
- **SSH Agent Forwarding** - Three approval modes: auto-approve, per-session, per-request
- **Secure Enclave Keys** - Ed25519, ECDSA, and RSA keys with biometric protection
- **Port Forwarding** - Local (`-L`) and remote (`-R`) TCP forwarding
- **Auto-start tmux** - Automatically attach to or create tmux sessions on connect
- **Tailscale Integration** - Device discovery and SSH to your tailnet with no-auth support
- **Host Shorthand (HSS)** - Pattern-based hostname expansion with YAML configuration

### YubiKey & FIDO2
- **YubiKey PIV** - SSH authentication with hardware-bound private keys via Lightning, NFC, or USB-C. Supports RSA, ECDSA, and Ed25519 (firmware 5.7+) with key generation directly on device
- **FIDO2 Security Keys** - Any FIDO2-compatible key (YubiKey 5, SoloKeys, etc.) for touch-to-sign SSH authentication using `webauthn-sk-ecdsa-sha2-nistp256@openssh.com`
- **Key Import** - Import existing SSH private keys to YubiKey PIV slots with optional keychain deletion
- **Smart PIN Caching** - Wired connections cache for the session; NFC connections cache across taps with session batching for multi-tab signing
- **iCloud Sync** - YubiKey references and FIDO2 credential metadata sync across devices; private keys never leave hardware

### Rootshell Roam
- **Mosh-Compatible Protocol** - Native [mosh](https://mosh.org)-compatible implementation built entirely in Swift with SSP (State Synchronization Protocol) support. Works with any standard mosh-server installation
- **tssh/trzsz Support** - [tssh](https://github.com/trzsz/trzsz-ssh) connections with UDP-based terminal transport offering full native scrollback and lower interactive latency than mosh
- **QUIC + KCP Transports** - Choose between QUIC (TLS 1.3, modern congestion control) or KCP (AES-GCM-256) for tssh transport. Configure in Settings → Roam → Transport Mode
- **Session Resumption** - Roam sessions survive app termination and device reboots. Credentials are stored in the Keychain and sessions resume automatically. tsshd reconnect support requires our [upstream PR](https://github.com/trzsz/tsshd/pull/16) ([fork](https://github.com/kitknox/tsshd))
- **Seamless Network Roaming** - Switch between WiFi and cellular without dropping your session. Handles IP address changes, network transitions, and temporary connectivity loss with a status banner
- **STUN Firewall Traversal** - Automatic NAT hole-punching via STUN to enable connections through stateful firewalls without VPN tunnels
- **Predictive Local Echo** - Keystroke predictions displayed immediately while waiting for server confirmation, making typing responsive on high-latency connections
- **Hardware-Accelerated Crypto** - Apple hardware-accelerated AES with key state caching for OCB encryption/decryption

### Cloud & Infrastructure
- **Cloud Providers** - AWS, Azure, Linode, DigitalOcean, Tailscale with OAuth authentication
- **Serial Console** - Direct access to Linode LISH and AWS EC2 serial consoles
- **Kubernetes** - Cluster browsing, node debugging via debug pods, EKS kubeconfig generation
- **Connection Profiles** - Save connections with tags, folders, and iCloud sync

### AI Integration
- **AI Agent** - Built-in assistant accessible via ⌘I in SSH sessions
  - Providers: Anthropic Claude, OpenAI, Google Gemini, OpenRouter
  - Web search and page fetch tools
  - Thinking model support with extended reasoning
- **MCP Server** - Connect external AI tools to execute SSH commands and access cloud resources

### Input & Interaction
- **Terminal Mouse Support** - Full mouse event passthrough for tmux, vim, zellij
- **Keyboard Shortcuts** - Fully customizable keybindings with menu bar integration
- **Touch Selection** - Single-finger drag to select, two-finger to scroll
- **Virtual Keyboard** - Tab key toolbar with double-tap for literal tab

### Sync & Persistence
- **iCloud Sync** - Connection history, known hosts, and profiles sync across devices
- **Local Shell** - Full terminal sessions on iOS and macOS

## Privacy

rootshell collects no analytics or crash data unless otherwise part of the TestFlight platform itself.

## Links

- [Website & Documentation](https://beta.rootshell.com)

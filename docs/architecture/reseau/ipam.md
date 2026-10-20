# IPAM

| VLAN | Zone           | Subnet          | Gateway      | Rôle                                                          |
| ---- | -------------- | --------------- | ------------ | ------------------------------------------------------------- |
| 10   | Management     | `10.0.10.0/24`  | `10.0.10.1`  | Équipements réseau                                            |
| 20   | Infrastructure | `10.0.20.0/24`  | `10.0.20.1`  | Hyperviseurs, serveur de backup, et services d'infrastructure |
| 30   | Compute        | `10.0.30.0/24`  | `10.0.30.1`  | Nodes Kubernetes et workload                                  |
| 40   | Storage        | `10.0.40.0/24`  | `10.0.40.1`  | NAS et stockages centralisés                                  |
| 50   | Users          | `10.0.50.0/24`  | `10.0.50.1`  | Utilisateurs permantents                                      |
| 60   | IoT            | `10.0.60.0/24`  | `10.0.60.1`  | Objets connectés avec connexion externe                       |
| 70   | NoT            | `10.0.70.0/24`  | `10.0.70.1`  | Objets connectés sans connexion externe                       |
| 80   | Guests         | `10.0.80.0/24`  | `10.0.80.1`  | WiFi invités                                                  |
| 99   | DMZ            | `10.0.99.0/24`  | `10.0.99.1`  | DMZ pour le reverse proxy                                     |
| N/A  | Proxmox Mesh   | `172.16.0.0/29` | Non-routable | Réseau mesh Proxmox HA                                        |

## VLAN 10 (Management)

### Pool Réseau

| IP          | Hostname        | Objet         | Fonction                 |
| ----------- | --------------- | ------------- | ------------------------ |
| `10.0.10.1` | phy-rtr-lvrm-01 | Routeur       | Routing/Pare-Feu/Gateway |
| `10.0.10.2` | phy-mdm-lvrm-01 | Modem         | Freebox                  |
| `10.0.10.3` | phy-ap-lvrm-01  | Point d'accès | Wi-Fi                    |
| `10.0.10.4` | phy-ap-ofce-01  | Point d'accès | Wi-Fi                    |
| `10.0.10.5` | phy-sw-lvrm-01  | Switch        | L3 10GbE                 |
| `10.0.10.6` | phy-sw-lvrm-02  | Switch        | L2 2,5GbE                |


## VLAN 20 (Infrastructure)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.20.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |

### Pool Hyperviseurs

| IP           | Hostname   | Objet       | Fonction       |
| ------------ | ---------- | ----------- | -------------- |
| `10.0.10.10` | phy-pve-01 | Hyperviseur | Virtualisation |
| `10.0.10.11` | phy-pve-02 | Hyperviseur | Virtualisation |
| `10.0.10.12` | phy-pve-03 | Hyperviseur | Virtualisation |
### Pool LXC

| IP           | Hostname              | Objet | Fonction                |
| ------------ | --------------------- | ----- | ----------------------- |
| `10.0.20.30` | lxc-dns-prd-deb13-01  | LXC   | DNS                     |
| `10.0.20.31` | lxc-pki-prd-deb13-01  | LXC   | PKI                     |
| `10.0.20.32` | lxc-vlt-prd-deb13-01  | LXC   | Gestionnaire de Secrets |

### Pool VM

| IP           | Hostname             | Objet | Fonction               |
| ------------ | -------------------- | ----- | ---------------------- |
| `10.0.20.60` | vm-glab-prd-deb13-01 | VM    | SCM                    |
| `10.0.20.61` | vm-iam-prd-deb13-01  | VM    | IdP + VPN              |
| `10.0.20.62` | vm-ntbx-prd-deb13-01 | VM    | DCIM + IPAM            |
| `10.0.20.63` | vm-grun-prd-deb13-01 | VM    | Gitlab Runner (Docker) |
| `10.0.20.64` | vm-ubqt-prd-deb13-01 | VM    | Ubiquiti Controller    |

## VLAN 30 (Compute)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.30.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |
### Pool Kubernetes (Dev + prod + mgmt)
 
À déterminer selon le nombre de nodes Kubernetes

### Pool Workload

| IP           | Hostname       | Objet   | Fonction   |
| ------------ | -------------- | ------- | ---------- |
| `10.0.30.20` | phy-ia-lvrm-01 | Serveur | Serveur IA |

## VLAN 40 (Storage)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.40.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |

### Pool NAS

| IP           | Hostname   | Objet | Fonction |
| ------------ | ---------- | ----- | -------- |
| `10.0.40.20` | phy-nas-01 | NAS   | Stockage |

## VLAN 50 (Users)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.50.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |

### Postes et appareils

Adresses réservées par DHCP. L'inventaire nominatif est tenu dans Netbox, hors de cette documentation publique.

## VLAN 60 (IoT)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.60.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |

### Objets connectés

Adresses réservées par DHCP. L'inventaire nominatif est tenu dans Netbox, hors de cette documentation publique.

## VLAN 70 (NoT)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.70.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |
## VLAN 80 (Guests)

### Pool Réseau

| IP          | Hostname        | Objet   | Fonction                 |
| ----------- | --------------- | ------- | ------------------------ |
| `10.0.80.1` | phy-rtr-lvrm-01 | Routeur | Routing/Pare-Feu/Gateway |
### Pool autre

DHCP

## VLAN 99 (DMZ)

| IP          | Hostname        | Objet        | Fonction                 |
| ----------- | --------------- | ------------ | ------------------------ |
| `10.0.99.1` | phy-rtr-lvrm-01 | Routeur      | Routing/Pare-Feu/Gateway |
| `10.0.99.2` | phy-rp-01       | Raspberry Pi | Reverse Proxy            |

## Non Routable

### Pool Hyperviseurs

| IP           | Hostname   | Objet       | Fonction       |
| ------------ | ---------- | ----------- | -------------- |
| `172.16.0.1` | phy-pve-01 | Hyperviseur | Virtualisation |
| `172.16.0.2` | phy-pve-02 | Hyperviseur | Virtualisation |
| `172.16.0.3` | phy-pve-03 | Hyperviseur | Virtualisation |

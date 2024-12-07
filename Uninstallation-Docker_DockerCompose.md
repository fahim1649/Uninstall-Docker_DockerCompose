```javascript
#!/bin/bash

# Remove Docker packages
echo "Removing Docker packages..."
for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do
  sudo apt-get remove -y $pkg
done

# Purge Docker CE packages
echo "Purging Docker CE packages..."
sudo apt-get purge -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-ce-rootless-extras

# Remove Docker data directories
echo "Removing Docker data directories..."
sudo rm -rf /var/lib/docker
sudo rm -rf /var/lib/containerd

# Remove Docker repository configuration
echo "Removing Docker repository configuration..."
sudo rm /etc/apt/sources.list.d/docker.list
sudo rm /etc/apt/keyrings/docker.asc

echo "Docker uninstallation complete."
```

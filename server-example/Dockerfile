FROM dimankiev/rehlds-cstrike:edge

# Copy everything from cstrike to temp location first
COPY ./cstrike /tmp/custom-cstrike

# Create necessary directories first
RUN mkdir -p /opt/steam/hlds/cstrike/addons/amxmodx/metamod && \
    mkdir -p /opt/steam/hlds/cstrike/addons/yapb && \
    mkdir -p /opt/steam/hlds/cstrike/addons/amxmodx/{configs,plugins,scripting,data} && \
    mkdir -p /opt/steam/hlds/cstrike/sound

# Install YaPB Bots if they exist
RUN if [ -d "/tmp/custom-cstrike/addons/yapb" ]; then \
      cp -rf /tmp/custom-cstrike/addons/yapb/* /opt/steam/hlds/cstrike/addons/yapb/ 2>/dev/null || true; \
    fi

# Create necessary directories first
RUN mkdir -p /opt/steam/hlds/cstrike/addons/amxmodx/metamod && \
    mkdir -p /opt/steam/hlds/cstrike/addons/yapb && \
    mkdir -p /opt/steam/hlds/cstrike/addons/amxmodx/{configs,plugins,scripting,data} && \
    mkdir -p /opt/steam/hlds/cstrike/sound

# Handle Metamod plugins.ini if it exists
RUN if [ -f "/tmp/custom-cstrike/addons/metamod/plugins.ini" ]; then \
      touch /opt/steam/hlds/cstrike/addons/amxmodx/metamod/plugins.ini && \
      cat /tmp/custom-cstrike/addons/metamod/plugins.ini >> /opt/steam/hlds/cstrike/addons/metamod/plugins.ini; \
    fi

# Install AMX Mod X files if they exist
RUN if [ -d "/tmp/custom-cstrike/addons/amxmodx/configs" ]; then \
      cp -rf /tmp/custom-cstrike/addons/amxmodx/configs/* /opt/steam/hlds/cstrike/addons/amxmodx/configs/ 2>/dev/null || true; \
    fi

RUN if [ -d "/tmp/custom-cstrike/addons/amxmodx/plugins" ]; then \
      cp -rf /tmp/custom-cstrike/addons/amxmodx/plugins/* /opt/steam/hlds/cstrike/addons/amxmodx/plugins/ 2>/dev/null || true; \
    fi

RUN if [ -d "/tmp/custom-cstrike/addons/amxmodx/scripting" ]; then \
      cp -rf /tmp/custom-cstrike/addons/amxmodx/scripting/* /opt/steam/hlds/cstrike/addons/amxmodx/scripting/ 2>/dev/null || true; \
    fi

RUN if [ -d "/tmp/custom-cstrike/addons/amxmodx/data" ]; then \
      cp -rf /tmp/custom-cstrike/addons/amxmodx/data/* /opt/steam/hlds/cstrike/addons/amxmodx/data/ 2>/dev/null || true; \
    fi

# Copy sound files if they exist
RUN if [ -d "/tmp/custom-cstrike/sound" ]; then \
      cp -rf /tmp/custom-cstrike/sound/* /opt/steam/hlds/cstrike/sound/ 2>/dev/null || true; \
    fi

# Copy any other custom files (maps, configs, etc.)
RUN find /tmp/custom-cstrike -type f \( ! -path "*/addons/*" ! -path "*/sound/*" \) -exec cp -f {} /opt/steam/hlds/cstrike/ \; 2>/dev/null || true

ENTRYPOINT ["./hlds_run", "-timeout 3", "-pingboost 1", "-game cstrike", "+map de_dust2", "+maxplayers 32"]

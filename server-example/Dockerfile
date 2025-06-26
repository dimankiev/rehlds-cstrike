FROM dimankiev/rehlds-cstrike

# Install YaPB Bots
COPY cstrike/addons/yapb /opt/steam/hlds/cstrike/addons/yapb

# Connect YaPB to Metamod
COPY cstrike/addons/metamod/plugins.ini /opt/steam/hlds/cstrike/addons/metamod/plugins-temp.ini
RUN cat /opt/steam/hlds/cstrike/addons/metamod/plugins-temp.ini >> /opt/steam/hlds/cstrike/addons/amxmodx/metamod/plugins.ini

# Remove temporary metamod plugins.ini
RUN rm /opt/steam/hlds/cstrike/addons/metamod/plugins-temp.ini

# Install amxmodx plugins
COPY cstrike/addons/amxmodx/configs /opt/steam/hlds/cstrike/addons/amxmodx
COPY cstrike/addons/amxmodx/plugins /opt/steam/hlds/cstrike/addons/amxmodx
COPY cstrike/addons/amxmodx/scripting /opt/steam/hlds/cstrike/addons/amxmodx
COPY cstrike/addons/amxmodx/data /opt/steam/hlds/cstrike/addons/amxmodx

# Copy amxmodx plugins dependencies
COPY cstrike/sound /opt/steam/hlds/cstrike

ENTRYPOINT ["./hlds_run", "-timeout 3", "-pingboost 1", "-game cstrike", "+map de_dust2", "+maxplayers 32"]

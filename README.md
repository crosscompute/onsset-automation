# OnSSET Automation

[OnSSET](https://onsset.readthedocs.io) is a model for electrification planning developed by the KTH School of Industrial Engineering and Management, Division of Energy Systems. This automation makes it easier to generate batch reports using the [CrossCompute Analytics Automation Framework](https://github.com/crosscompute/crosscompute).

![Output Screenshot](https://user-images.githubusercontent.com/266668/150619736-f469fdb2-e8df-464b-b357-c2ba36f884db.png)

## Serve Automation

```bash
sudo dnf -y install python3.9
# sudo apt -y install python3.9

python3.9 -m venv ~/.virtualenvs/crosscompute
source ~/.virtualenvs/crosscompute/bin/activate

pip install --upgrade \
    crosscompute>=0.9.1 \
    crosscompute-views-map>=0.0.2

cd ~/Documents
git clone https://github.com/crosscompute/onsset-automation
cd onsset-automation
bash setup.sh

export MAPBOX_TOKEN=YOUR-MAPBOX-TOKEN

crosscompute
```

## Add Batches

First, create the batch folders:

```bash
cp -r batches/djibouti batches/lesotho
libreoffice batches/lesotho/scenario-info.csv
libreoffice batches/lesotho/scenario-parameters.csv
libreoffice batches/lesotho/specs-data.csv
libreoffice batches/lesotho/settlements.csv
```

Then, update the configuration file:

```bash
vim automate.yml

  batches:
  - name: Djibouti
    folder: batches/djibouti
  - name: Lesotho
    folder: batches/lesotho
```

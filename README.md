# nolus snepshot


 # Instructions
Stop the service and reset the data
```
sudo systemctl stop nolusd
cp $HOME/.nolus/data/priv_validator_state.json $HOME/.nolus/priv_validator_state.json.backup
rm -rf $HOME/.nolus/data
```
Download latest snapshot
```
wget http://95.216.221.119:8000/nolusdata.tar.gz 
tar -C $HOME/ -zxvf nolusdata.tar.gz --strip-components 1
mv $HOME/.nolus/priv_validator_state.json.backup $HOME/.nolus/data/priv_validator_state.json
```
Restart the service and check the log
```
sudo systemctl start nolusd && sudo journalctl -u nolusd -f --no-hostname -o cat
```

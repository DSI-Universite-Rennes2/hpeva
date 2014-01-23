hpeva
=====

hpeva external storage module for ganeti


### PURPOSE

 This modules makes ganeti external storage module to work with HP EVAs Systems

### PREREQUISITE
 * cluiclient downloadable in HP Replication Solution Manager Software (http://h20565.www2.hp.com/portal/site/hpsc/template.PAGE/public/psi/swdDetails/?sp4ts.oid=3807693&spf_p.tpst=swdMain&spf_p.prp_swdMain=wsrp-navigationalState%3DswItem%253Dco_51723_1&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken)
 * openjdk-jre (for cluiclient)

### INSTALL :
 * Copy this directory in ExtStorage Providers search path (/srv/ganeti/extstorage, /usr/local/lib/ganeti/extstorage, /usr/lib/ganeti/extstorage, /usr/share/ganeti/extstorage)

 * Copy and complete eva.conf in /etc/ganeti/extstorage/

 * Copy cluiclient wherever you want and adapt config file

 * Patch function NewUUID() in  /usr/share/ganeti/ganeti/utils/io.py to match this one :

    def NewUUID():
      """Returns a random UUID.
   
      @note: This is a Linux-specific method as it uses the /proc filesystem.
      @rtype: str
   
      """
      return ReadFile(constants.RANDOM_UUID_FILE, size=18).rstrip("\n")

 * restart ganeti


### TODO
  - Grow function : It seems that cluiclient does not want to resize a VD with thin provisionning disabled.


对于初始操作，此阶段将发生在主系统操作之前。<br /><br />可利用此机会包括逻辑，以在数据库事务前取消操作。<br /><br />由在其他阶段中注册的扩展触发的后续操作也将会通过此阶段，但将包括在调用扩展的事务内。<br /><br />此阶段在执行任何安全检查之前发生，以验证发出调用的用户或登录用户是否具有执行预期操作所需的正确权限。
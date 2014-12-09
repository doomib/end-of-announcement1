Routing:
<?php 
Route::set('site_announcements/profile/announcements/zakoncz', TRUE, array('id' => '[0-9]+'))
			->defaults(array(
				'directory'	 => 'profile',
				'controller'	=> 'announcements',
				'action'		=> 'zakoncz'
			)); 
			?>
			model:
		<?php
		public function zakoncz()
	{
		if ( ! $this->_loaded)
			throw new Kohana_Exception('Cannot delete :model model because it is not loaded.', array(':model' => $this->_object_name));
		$this->annoucement_availability = date('Y-m-d H:i');
		
		$this->save();
		$this->clear();
		return $this;
	}
	?>
	controler:
	public function action_zakoncz() 
	{
		$announcement = ORM::factory('Announcement')
			->get_user_announcement($this->request->param('id'), $this->_auth->get_user_id());

		if (!$announcement->loaded()) 
		{
			throw new Http_Exception_404();
		}
 
		$announcement->zakoncz();

		flashinfo::add(___('announcements.profile.delete.success'), 'success');

		$this->redirect_referrer();
	}
	widok - wywołanie akcji:
	<?php 
	echo Route::url('site_announcements/profile/announcements/delete', array('id' => $a->annoucement_id)) 
	?>
